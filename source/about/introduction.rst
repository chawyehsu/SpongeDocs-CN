============
项目介绍
============

Sponge 是什么？
~~~~~~~~~~~~~~~

Sponge 项目的目的是建立一个 Minecraft 的插件开发环境。Sponge 是在全球性的社区中诞生的，它的开源自然也意味着任何人都可以参与其中。

在目睹 Minecraft 插件开发社区中其它项目的失败后，Sponge 诞生了。我们试图避免犯下那些失败项目的错误，因此：

* Sponge 是完全开源的。
* Sponge 基于 MIT 授权许可 —— 一个极其开放的开源许可。
* 性能是高优先考虑的。

大多数基于 Sponge API 开发的插件可以不加修改地在数个不同版本的 Minecraft 中运行工作。这意味着，服主们几乎不再需要担心插件的不兼容性。

除了 Sponge API 外我们还拥有另外两个项目：

(1) **SpongeForge**，这是一个 Minecraft Forge 的核心模组，Minecraft Forge 是一个著名的 Minecraft 模组化框架，是目前 Minecraft
    模组界的主导。但 Forge 缺少跨版本的 API，而这则是 Sponge 要做的。Sponge 能让服主们更轻松简单地部署插件和管理服务器。

(2) **SpongeVanilla**，一个运行于原版 Minecraft 服务器上的 Sponge API 独立实现。（SpongeVanilla 的前身是 Granite，后面开发团队合并了）

在 SpongeForge 或 SpongeVanilla 服务器中的玩家无需安装任何的客户端模组。玩家使用 Mojang 提供的原版 Minecraft 客户端即可登录到
Sponge 服务器。

Sponge API 不限定于具体的平台。也就是说服主们可以在任何一个 Sponge API 的官方实现中运行 Sponge 插件。根据 Sponge
的通用功能 mixins，在 2 种不同的官方实现下 Sponge 插件的功能是一致的。

从哪里可以下载 Sponge？
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

SpongeForge 和 SpongeVanilla 都仍在开发阶段，开发版可以在 :doc:`/downloads` 页面获取。

Sponge 的幕后
~~~~~~~~~~~~~~~~~~~~~

这个项目目前由 blood，gabizou 以及 Zidane 主导进行。我们力图使整个团队开放起来，以确保项目主管不会最终“紧握所有权利”。尽管如此，
这三位主管拥有最终决定权，以保证项目的高效运作。

完整的工作人员列表请查看 :doc:`staff` 页面。

我们的开发者都精通 Java，并且他们中的许多人已有多年的 Minecraft 开发经验，熟悉其机制的来龙去脉。有太多优秀开发者参与到 Sponge
项目中了，所以我们不能够一一列出它们的名字！
