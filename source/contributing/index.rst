======================
向 Sponge 做贡献
======================

本章节旨在告诉你如何参与到 Sponge 中。

我可以帮助哪些项目？
======================================

Sponge 项目及其组成部分在 `GitHub <https://github.com/spongepowered>`_ 上进行维护。如果你对 GitHub 与 git
工具不太熟悉，可以先看看 :doc:`howtogit`。在开始所有工作之前，强烈建议你先阅读我们的 :doc:`guidelines`
。我们目前正在维护着以下几个项目：

* SpongeAPI
* SpongeForge
* SpongeVanilla
* SpongeCommon
* Mixin
* SpongeDocs
* Ore

如果你想了解更多关于该项目的架构以及各个部分是如何联系在一起的，可以前往查阅 :doc:`../about/structure`。

需要什么样的帮助？
============================

基本的贡献
~~~~~~~~~~~~~~~~~~~

以下是几乎每个人都可以完成的。你不需要了解诸如 Java 或 Python 的编程语言：

* 测试 SpongeForge 或者 SpongeVanilla 并报告漏洞或者使用异常
* 报告或者建议你遇到的任何错误、故障或者漏洞。
* 发表可以让 Sponge 变得更好的建议或者意见。

通过我们的 `GitHub 仓库 <https://github.com/spongepowered/>`_ 来报告漏洞，和我们的
`论坛 <https://forums.spongepowered.org/>`_ 来提供建议。查看我们的
:doc:`Bug Reporting page <../server/spongineer/bugreport>` 以获取更多的信息。

中级的贡献
~~~~~~~~~~~~~~~~~~~~~~~~~~

你应该至少具备 Java、Python 或 reST 语言的基础知识来帮助我们完成以下的工作：

* 帮助修复漏洞
* 完成 API 的实现（SpongeForge 与 SpongeVanilla）
* :doc:`帮助撰写 SpongeDocs <spongedocs>`
* 帮助 `在 Crowdin 上翻译文档 <https://crowdin.com/project/sponge-docs>`_
* 帮助发展 Ore

`Sponge API <https://github.com/spongepowered/SpongeAPI>`_，`SpongeForge
<https://github.com/spongepowered/SpongeForge>`_，`SpongeVanilla
<https://github.com/spongepowered/SpongeVanilla>`_ 和
`Ore <https://github.com/spongepowered/Ore>`_ 以及 `SpongeDocs
<https://github.com/spongepowered/SpongeDocs>`_ 的开发是在托管于 GitHub 上的几个仓库中进行的。

高级的贡献
~~~~~~~~~~~~~~~~~~~~~~

最后，以下是你能提供帮助的最困难的事情。在尝试提供帮助之前，强烈建议你具备 Java 和 Minecraft
的高级知识，同时至少具备 `Sponge API <https://github.com/spongepowered/SpongeAPI>`_
及其 `架构 <https://jd.spongepowered.org>`_ 的基础知识：

* 向 API 中增加功能（:doc:`implementation/pr`）
* 在实现中实现高级的 API 功能

目录
========

.. toctree::
    :maxdepth: 2
    :titlesonly:

    guidelines
    howtogit
    implementation/index
    spongedocs
    porting
    versioning
