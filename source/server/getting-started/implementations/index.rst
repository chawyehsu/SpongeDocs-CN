==========================
选择一个实现
==========================

*实现* 就是运行 Sponge 插件的载体。只要是正确地使用 ``SpongeAPI``
开发出来的插件，就应该能在任何一个充分完整的实现上正确地运行。

Minecraft 不能开箱即用地运行 Sponge 插件，但修改后可以。

Sponge API 本身是一个 `开放式标准 <https://github.com/SpongePowered/SpongeAPI>`__。

可用的实现
=========================

目前有两种实现：

+--------------------------------------+--------------------------------------------------+
| 名称                                 | 基于                                             |
+======================================+==================================================+
| :doc:`SpongeForge <spongeforge>`     | Mojang 的原版 Minecraft 以及 Minecraft Forge     |
+--------------------------------------+--------------------------------------------------+
| :doc:`SpongeVanilla <spongevanilla>` | Mojang 的原版 Minecraft                          |
+--------------------------------------+--------------------------------------------------+


我应该选择哪一个？
~~~~~~~~~~~~~~~~~~

如果你想要运行依赖 MinecraftForge 的模组，或者你希望在单人游戏下使用
Sponge，那么请选择 :doc:`SpongeForge <spongeforge>`。

如果你只想在 Mincraft 服务器上使用插件（不使用模组），那么你可以选择
:doc:`SpongeForge <spongeforge>` 或 :doc:`SpongeVanilla
<spongevanilla>`。SpongeForge 支持原版客户端，只要你不安装那些需要客户端模组的 Forge
模组。如果你更喜欢运行没有 Forge 的服务器，那么 SpongeVanilla 会是你的首选。

SpongeVanilla 和
SpongeForge（没有模组时）的行为相同，所以在两者之间选择是见仁见智的问题，而不是因功能或特性而进行选择。

目录
========

.. toctree::
    :maxdepth: 2
    :titlesonly:

    spongeforge
    spongevanilla
