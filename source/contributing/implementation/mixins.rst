======
Mixins
======

.. note::
   本页面适用于 SpongeCommon、SpongeForge 和 SpongeVanilla，这三个仓库利用了 Mixins
   来挂钩底层实现（原版 Minecraft 服务器和 Forge)。

Mixins 是一种在运行时通过向类中添加额外的行为来修改 Java 代码的方式。这使得我们能够将预期的行为移植进已有的
Minecraft 对象中。所有的官方 Sponge 实现都需要 Mixins 才能运行。

`Mixin Wiki <https://github.com/SpongePowered/Mixin/wiki/>`__ 上对一些支撑 Mixins 工作的核心概念进行了基本的介绍。

*上述 Wiki 的开始相当基础。如果你是一位有经验的 Java 开发者，可以直接跳到第 4 节，那里才真正讨论 mixins 本身。*

如果你打算开始写 mixins，我们强烈推荐先仔细研究在 `SpongeForge 仓库
<https://github.com/SpongePowered/Sponge/tree/master/src/example/java/org/spongepowered>`__
中的所有例子，它们有大量的注释并且覆盖了许多更复杂的情形。你也可以参考 Mixin 本身的
Javadoc，几乎所有东西都已经有文档了。

**警告：向 mixins 做贡献时，请注意你不能使用匿名类或 lambda 表达式。**

换言之类似于以下的一些表示将会给 mixins 带来可怕与致命的失败，还会毁坏所有尝试使用 Sponge 的上层。

.. code-block:: java

    return new Predicate<ItemStack>() {
        @Override
        public boolean test(ItemStack input) {
            return input.getItem().equals(Items.golden_apple);
        }
    }

.. code-block:: java

    return input -> input.getItem().equals(Items.golden_apple);

.. code-block:: java

    return this::checkItem;

这适用于所有带有 ``@Mixin`` 注解的类。而不被 mixin
处理器访问到的类则可以使用那些功能。不过，你可以使用一个静态的工具类来创建匿名类，因为不像
mixin 类那样会被合并进特定的目标类，工具类仍然会存在于运行时中。所以下面的代码将会工作。

.. code-block:: java

    public class ItemUtil {
        public static Predicate<ItemStack> typeChecker(final Item item) {
            return new Predicate<ItemStack>() {
                @Override
                public boolean test(ItemStack input) {
                    return input.getItem().equals(item);
                }
            }
        }
    }

    @Mixin(TargetClass.class)
    public abstract class SomeMixin {
        public Predicate<ItemStack> someFunction() {
            return ItemUtil.typeChecker(Items.golden_apple);
        }
    }

.. note::

  Mixin 项目除了供 Sponge 本身使用外，也为其它很多项目所用。所以 Mixin 有其自己的仓库与文档。
