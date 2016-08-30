=================
如何使用 Git(Hub)
=================

如果你想协助开发 Sponge，或者你对 API 有一个好的补充，又或者你想改进我们的文档，那么你需要熟悉
``git`` 以及 GitHub。如果你已经熟悉派生（Fork）、分支（Branch）、Issue、拉取请求（Pull
Request）以及提交（Commit），那么你可以跳过本文。如果你不清楚我们在说些什么的话，请接着读下去。

.. note::
  本指南假定你已经阅读了 :doc:`../preparing/git` 并且已经在你的机器上配置好了你所选择的 Git 客户端。

Git 和 GitHub 的基本概念
===================================

Git 允许众多不同的开发者在同一时间开发同一个软件。GitHub
是一个网站，开发者可以在上面进行协作，并与他人共享他们的工作。GitHub 依赖 Git 来管理前述的工作。

.. tip::
  如果你不熟悉 Git 和 GitHub 的词汇，可以看看 `GitHub 的术语表页面 <https://help.github.com/articles/github-glossary/>`_。

.. image:: /images/contributing/repo-overview.svg
    :alt: Repo Overview

如上图所示，一个仓库被命名为“SpongePowered”，拥有两个分别名为“master”和“feature
1”的分支，和其上的若干提交。

让我们将上述项作为背景——以这个 *仓库* 开始吧。 仓库是一个存放项目文件的地方。 SpongePowered
的仓库位于 `GitHub <http://github.com/spongepowered>`__
上。然而，这个仓库被设定了一些访问控制以保护它免受意外或恶意的更改。该仓库对一般用户是只读
的，所以你不能简单地自己去做更改。现在你可能在想你应该如何提交建议及更改。嗯，这时候该 *派生*
发挥作用了。你可以得到一份 SpongePowered 仓库的副本，并能在上面做更改。完成更改后，以此向我们的仓库发送一个
拉取请求（*PR*）。之后你的增改建议将会被检查，如果出现错误或有需要改进的地方，工作人员会告知你，最后 PR 将会被合并。

在我们详细说之前，先简短概括一下上述流程：

1. 派生你所选择的仓库
#. 克隆仓库到你的本地机器上
#. 创建一个新的分支
#. 做出你期望的更改
#. 测试是否工作
#. 提交更改
#. 同步到 GitHub 上
#. 向 SpongePowered 仓库提出一个 PR
#. 若 PR 有修订需要则进行修订
#. 工作人员将你的 PR 合并进 master 分支

请看详情！
===============

1. 派生一个仓库
~~~~~~~~~~~~~~~~~

.. note::
  如果你对你正在更改的仓库没有推送（push）权利，那这一个步骤是必须的。如果你正在你自己的仓库中进行
  工作，则无需派生。跳过本步骤直接 ``克隆（clone）`` 即可。如果你正在对 Sponge 做更改，而你 **不是**
  工作人员，则本步骤是必须的。

既然你知道了基本的概念，我们继续讨论细节。首先你需要派生你想要进行更改的仓库。在 GitHub.com
上，你能在仓库页面的顶部找到一个 ``Fork`` 按钮。点击它，GitHub
将会进行一些工作并向你呈现一份原始仓库的克隆。然后你会发现这份克隆位于
``你的 GitHub 帐号/克隆仓库名`` 下。好了，第一个步骤已完成。


.. note::
  原始仓库的所有分支也会被派生，你会得到一份完整的仓库克隆。

.. image:: /images/contributing/repo-fork.svg
    :alt: Repo forking

2. 将派生克隆到你的本地机器
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

现在你需要将派生仓库克隆到你的本地机器中以进行更改。打开你选用的 Git
客户端（:doc:`../preparing/git`）并将派生仓库 ``克隆``
到你的本地机器。客户端会向你询问存储的文件夹。至此第二个步骤完成了，做得好！

.. note::
  大多数步骤可以通过你选用的图形用户界面（GUI）完成。如果你熟悉命令行界面，你也可以使用命令行。每个
  步骤会显示你所需要的以达到预期结果的命令。

或者你可以使用 CLI（命令行界面，Windows 上的 ``CMD`` 或 ``powershell``）。注意，在你键入该命令之前，你需要
自行创建存储的文件夹：

.. code-block:: none

  git clone git://github.com/你的 GitHub 帐号/克隆仓库名.git

.. image:: /images/contributing/repo-clone.svg
    :alt: Repo cloning

3. 创建一个新的分支
~~~~~~~~~~~~~~~~~~~~~~~~

现在你有了派生仓库的一个本地的克隆，是时候创建一个分支进行工作了。分支被设计用于在同一时间能够进行不
同特性或增改的开发与测试工作，而不会由于增改的干扰产生问题或错误。强烈建议你 **不要** 在 ``master``
分支上做更改。而是自己（以一个适当的名字）创建一个新的分支并在其中做更改。

这意味着我们首先需要创建一个 ``分支``，那就开始吧！你可以使用你的客户端（某处应该会有一个
``创建分支`` 的按钮），或者使用 git 命令行：

.. code-block:: none

  git checkout -b [新分支的名字]

这将会以你给出的名字创建一个 ``分支``
并切换到此分支。你要做的所有更改都将在此分支上。如果你需要切换到另一个分支（例如 ``master``
分支），重复使用这个命令即可。第三个步骤完成了！至此做得不错！要查看你的分支概况，仅需在你的
git 客户端上查看或者使用：

.. code-block:: none

  git branch

.. image:: /images/contributing/repo-branch.svg
    :alt: Branches

**现在可以做更改了**。用你选择的编辑器或者 IDE 开始吧。

4. 测试你的更改是否工作
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

对于 SpongeAPI 及其实现，你必须执行
``gradle compileJava``。如果无错完成，则继续下一个步骤。如果不是，进行适当的修正并重试。

对于 SpongeDocs 则可以提交你的 PR 了。它会自动进行构建并显示可能的错误。另一种选择是在本地进行构建。在
`SpongeDocs 的 Readme.md <https://github.com/SpongePowered/SpongeDocs/blob/master/README.md>`_
中可以查看进一步的说明。

5. 提交更改
~~~~~~~~~~~~~~~~~~~~~

完成更改后，你需要将更改捆绑成一个独立的包（一次 ``提交``）并将其应用到分支中。你的 git
客户端会再次帮助到你。给你的提交添加一个有意义的名字，如果有需要还可以附上一个简短的描述。这一个步骤也可使用
CLI 来完成：

首先收集所有你想要提交的文件及文件夹：

.. code-block:: none

  git add <文件>
  git add <文件夹>

现在这些文件已经被添加到了提交的更改列表中，执行：

.. code-block:: none

  git commit

这将会打开一个文本窗口，如果你愿意你可以在其中添加一条消息。看看下图，你会注意到，你的提交当前只存储
在本地，而不是在 GitHub 上你的派生仓库中。

.. note::
  在一个 PR 中可以有多个提交。对所有你需要更改的文件进行更改并提交更改。之后你可以将多个提交合并成一个提交。

至此，第六个步骤完成了。差不多了！

.. image:: /images/contributing/repo-commit.svg
    :alt: Committing

6. 同步到 GitHub 上
~~~~~~~~~~~~~~~~~~~

现在需要将更改应用到 GitHub 上你的派生仓库中。目前你做过的所有更改只存储在本地。一如既往地，你可以使用你的
git 客户端进行操作（你的 GUI 某处会有相应的按钮），或者你可以使用 CLI：

.. code-block:: none

  git push <远程> <分支>

在本例中则应该是：

.. code-block:: none

 git push origin feature/YourFeature

.. image:: /images/contributing/repo-push.svg
    :alt: Pushing commits

7. 向 SpongePowered 仓库提出一个 PR
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

你可以通过 GitHub.com 上你的派生仓库的页面（你的派生仓库的页面顶部应该会有一个指引你的通知）或者使用
GitHub 客户端创建拉取请求。GitHub 官方的 Windows 客户端的这个功能在窗口的右上角。

.. image:: /images/contributing/repo-pr.svg
    :alt: PRs

8. 若 PR 有修订需要则进行修订
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

如果我们想要你对你的 PR 进行更改，你只需要直接在分支上做更多提交即可。后续的提交会自动地追加到你的 PR 中。

9. 你的 PR 被合并
~~~~~~~~~~~~~~~~~~~~~~

就是这样。我们完成了！太棒了！

Git 进阶
============

压缩（Squashing）与变基（Rebase）
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

比方说你已经完成了对仓库的增改，我们假定你在完成时一共做了 137 次的提交。你的提交历史看起来肯定会很乱
。如果提交历史就这样记录在仓库中，是否会有点羞耻感？而且太多琐碎的提交也会搞乱整个项目的提交历史。幸运的是
Git 有一个很好的工具来规避这类情况，这个工具叫 ``变基``。变基可以将你的 137
次小提交转化为一次大提交。这太棒了，是吧？为避免重新造轮子，这里我们只提供一个简短易明的压缩教程的链接给你：

`Gitready: 压缩与变基 <http://gitready.com/advanced/2009/02/10/squashing-commits-with-rebase.html>`_

下图就是压缩的过程，很直观吧：

.. image:: /images/contributing/repo-squash.svg
    :alt: Squashing commits

配置远程仓库
~~~~~~~~~~~~~~~~~~~

自然地，原始仓库是你的派生仓库的直接父级，同时你的派生仓库又是你的本地克隆的直接父级。但是，原始仓库
却 **不是** 你的本地克隆的直接父级。刚开始时这没有什么问题，但这却妨碍了你在本地克隆获取原始仓库最新的更
改。如果你配置了原始仓库作为你的本地克隆的一个远程仓库（即：``父级``），那么你就能够从原始仓库抓取所有更
改并应用到你的本地克隆中。下面看看抓取和更新是如何工作的：

.. image:: /images/contributing/repo-remote.svg
    :alt: Setting up a remote

好吧。这一个步骤只能通过 CLI 来完成，因为大多数 GUI 都缺少这一（太过高级的）功能：

.. code-block:: none

 git remote add upstream https://github.com/原始仓库拥有者/原始仓库名.git

如果你不确定这样是否工作，又或者你想检查当前已配置的远程仓库，你可以执行︰

.. code-block:: none

 git remote -v

输出大致如下：

.. code-block:: none

 origin    https://github.com/你的用户名/你的派生仓库.git (fetch)
 origin    https://github.com/你的用户名/你的派生仓库.git (push)
 upstream  https://github.com/原始仓库拥有者/原始仓库名.git (fetch)
 upstream  https://github.com/原始仓库拥有者/原始仓库名.git (push)

.. note::
  如果你看到 ``fatal: The current branch YourBranchName has no upstream branch.``
  的警告，则可能是该分支不在上游远程仓库中。这种情况可能会在你推送一个新分支的第一次提交时发生。这时可以使用
  ``git push --set-upstream origin 你的分支名`` 来配置 origin 作为上游并推送当前分支。

变基
~~~~~~~~

比如说你对你期望的分支做了一些更改，但同时其他人更新了远程仓库。也就是说你的派生仓库及本地克隆已经过
时了。这没什么大问题，但是为了在后期合并你的增改时避免出现问题，强烈建议你根据远程仓库的最新更改对你
的更改做 ``变基`` 操作。如果你还没配置远程仓库，在尝试做变基之前请先进行配置。

一次成功的变基需要几个步骤：

1. 从远程仓库抓取更改
---------------------------------------

首先你需要从远程仓库抓取更改。这一个步骤（再次）使用 CLI 来完成：

.. code-block:: none

 git fetch upstream

这将会得到远程 ``上游`` 的所有更改，并放入一个临时的 ``upstream/master`` 分支中。

2. 在本地合并远程仓库的更改
-------------------------------
现在需要先选择本地的 ``master`` 分支：

.. code-block:: none

 git checkout master

然后将 ``upstream/master`` 中的所有更改合并进本地的 ``master`` 分支：

.. code-block:: none

 git merge upstream/master

好了，下图就是至此我们所做的：

.. image:: /images/contributing/repo-rebase1.svg
  :alt: Rebasing 1

3. 根据更新后的 master 分支对本地分支做变基
---------------------------------------------
下一个步骤就是根据本地的 ``master`` 分支对你正在工作的本地分支做变基操作。这需要切换到你正在工作的分支上
（本例：``feature/yourfeature``）并执行变基操作。如下：

.. code-block:: none

 git checkout feature/yourfeature
 git rebase master

这将会回退你的分支，然后添加来自 master 的提交，之后再重新应用你做过的更改。结果如下：

.. image:: /images/contributing/repo-rebase2.svg
  :alt: Rebasing 2

4. 将内容推送到你的派生仓库
-------------------------------

最后一个步骤就是将所有内容推送到派生仓库中。如果你已经创建了一个 PR，则其会自动进行更新：

.. code-block:: none

 git checkout master
 git push -f
 git checkout feature/yourfeature
 git push -f

.. image:: /images/contributing/repo-rebase3.svg
  :alt: Rebasing 3

你做到了，太棒了！做得好，感谢乘坐变基航空（Rebase-Air）！
