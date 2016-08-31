=======================
贡献指南
=======================

我们需要开发者来帮助我们改进 SpongeAPI。完美的项目是不存在的，并且总有地方可以改进。如果你是一名开发
者并且有兴趣提供帮助，请不要犹豫。只需确保你跟随我们的指南即可。

大体步骤
=============

1. 按照 :doc:`../../preparing/index` 中的描述建立你的工作区。

#. 请确保你熟悉 Git 和 GitHub。如果你需要更新你的知识，看看这里： :doc:`howtogit`

#. 请先检查在 `SpongeAPI <https://github.com/SpongePowered/SpongeAPI/issues>`_，`SpongeCommon
   <https://github.com/SpongePowered/SpongeCommon>`_，`SpongeForge
   <https://github.com/SpongePowered/SpongeForge>`_，`SpongeVanilla
   <https://github.com/SpongePowered/SpongeVanilla>`_ 和 `SpongeDocs
   <https://github.com/SpongePowered/SpongeDocs>`_ 仓库中已有的
   Issue。可能已经有其他人正在进行相同的工作。你也可以检查一下那些 `被标记为 "help wanted" 的 issues
   <https://github.com/SpongePowered/SpongeAPI/labels/help%20wanted>`_，查找其中需要帮助的部分。

.. note::
    请不要为小于 20 行的小更改提交拉取请求（pull request），而是 `加入 #sponge IRC 频道（irc.esper.net）
    <https://webchat.esper.net/?channels=sponge>`_ 或 `加入 #spongedev IRC 频道（irc.esper.net）
    <https://webchat.esper.net/?channels=spongedev>`_，我们会结合其它小更改一起进行更改。

4. 如果一个 Issue 需要进行大更改，请在做更改之前开 Issue，这样我们就能够确认这个 Issue
   并知道你正在修正它。同时你应该尽早创建一个带有 ``[WIP]`` 前缀的
   WIP（Work In Progress，工作进行中）拉取请求，这样我们可以提前开始对其进行评审工作。

#. 派生（Fork）一个项目，克隆（clone）它并在一个额外的分支（branch）中进行你的更改操作。

#. 测试你的更改（至少能编译！），提交（commit）并推送（push）到你自己的派生仓库中。

#. 提交拉取请求时请附上一个简短的概述，说明你做了什么更改以及为什么要那样更改。

#. 如果你做了额外的更改，请将新提交推送到你的分支中。**不要压缩（squash）你的更改**，那会使得与你此前
   的拉取请求对比所做的更改变得极其困难。

#. 请确保你的 PR（Pull Request）已经变基（rebase）到当前你想要合并的分支的最新更改处。如果你需要变基相关帮助，请询问！

.. tip::
  如果你不确定你应该在哪个分支的基础上开始工作，请在提交你的 PR 之前查阅我们的 :doc:`versioning`。
