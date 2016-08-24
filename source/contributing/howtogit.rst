=================
如何使用 Git(Hub)
=================

如果你想协助开发 Sponge，或者你对 API 有一个好的补充，又或者你想改进我们的文档，那么你将需要熟悉
``git`` 以及 GitHub。如果你已经熟悉 Forking、Branches、Issues、Pull Requests 以及 Commits
，那么你可以跳过本文。如果你不清楚我们在说些什么的话，请接着读下去。

.. note::
  本指南假定你已经阅读了 :doc:`../preparing/git` 并且已经在你的机器上配置好了你所选择的 Git 客户端。

Git 和 GitHub 的基本概念
===================================

Git 允许许多不同的开发者在同一时间开发同一个软件。GitHub
是一个网站，开发者可以在上面进行协助，并与他人共享他们的工作。GitHub 依赖 Git 来管理上述的工作。

.. tip::
  如果你不熟悉 Git 和 GitHub 的词汇，可以看看 `GitHub 的术语表页面 <https://help.github.com/articles/github-glossary/>`_。

.. image:: /images/contributing/repo-overview.svg
    :alt: Repo Overview

如上图所示，该仓库名被命名为“SpongePowered”，拥有两个分别名为“master”和“feature
1”的分支，和其上的若干提交。

让我们将上述项作为背景——以这个 *仓库* 开始吧。 仓库是一个存放项目文件的地方。 SpongePowered
的仓库位于 `GitHub <http://github.com/spongepowered>`__
上。然而，这个仓库被设定了一些访问控制以保护它免受意外或恶意的更改。该仓库对一般用户是只读
的，所以你不能简单地自己去做更改。现在你可能在想你应该如何提交建议及更改。嗯，这时候该 *Fork*
发挥作用了。你可以得到一份 SpongePowered 仓库的副本，并能在上面做更改。完成更改后，以此向我们的仓库发送一个
拉取请求（*PR*）。之后你的增改建议将会被检查，如果出现错误或有需要改进的地方，工作人员会告知你，最后 PR 将会被合并。

在我们详细说之前，先简短概括一下上述流程：

1. Fork the repo of your choice
#. Clone it to your local machine
#. Create a new branch
#. Make the desired changes
#. Test if everything works
#. Commit the changes
#. Sync them to GitHub
#. Propose the changes in a PR to the SpongePowered Repo
#. Amend to your PR if necessary
#. Your PR gets pulled into master by staff

Details please!
===============

1. Forking a Repo
~~~~~~~~~~~~~~~~~

.. note::
  This step is only required if you don't have push rights on the repo you're making changes to. If you're working on
  your own repo, no fork is required. Just skip this step and ``clone`` directly. If you're making changes to Sponge
  and you **aren't** staff, this step is required.

Now that you know the basic concept, we'll discuss the details. First you need to fork the repository you want to
make changes to. This can be done on GitHub.com, where you'll find a ``Fork`` button at the top of the repositories page.
After pressing it, GitHub will do some work and present a clone of the original repo to you. You'll notice that the
clone is now located at ``YourGitHubAccount/ClonedRepoName``. Alright, first step completed.


.. note::
  All branches from the original repository will get forked too, you recieve an exact clone of the forked repo.

.. image:: /images/contributing/repo-fork.svg
    :alt: Repo forking

2. Cloning the Fork to Your local Machine
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Now you need to get this fork to your local machine to make your changes. Open the Git Client of your choice
(:doc:`../preparing/git`) and ``clone`` your fork to your local machine. The client will ask you for a folder to store
everything in. Second step finished, well done!

.. note::
  Most steps can be done via GUI of your choice. If you're experienced with a command line interface, then you can use
  it too. Each steps will show you the required commands to achieve the desired result.

Alternatively you can do this via CLI (command line interface, ``CMD`` or ``powershell`` on windows). Note
that you need to create the folder everything is getting cloned to yourself before typing this command:

.. code-block:: none

  git clone git://github.com/YourGitHubAccount/ClonedRepoName.git

.. image:: /images/contributing/repo-clone.svg
    :alt: Repo cloning

3. Creating a New Branch
~~~~~~~~~~~~~~~~~~~~~~~~

Now that you have a local clone of your fork, it's time to create a branch to work on. Branches were designed to be able
to develop and test different features or additions at the same time, without causing problems and errors due to
interferences of the additions. It's strongly advised that you **don't** make your changes on the ``master`` branch.
Instead, create a new branch yourself (with a sensible name) and make the changes there.

This implies that we need to create a ``branch`` first, so let's go! You can do this via your client (there
should be a ``create branch`` button somewhere), or you can use the CLI with git:

.. code-block:: none

  git checkout -b [name_of_your_new_branch]

This will create a ``branch`` with the name of your choice and switch to it. All changes you're about to make will be
on this branch. If you need to switch to another branch ( for example ``master``), just reuse this command. Third step
done! Good job so far! To get an overview of your branches, just have a look at your git client or use:

.. code-block:: none

  git branch

.. image:: /images/contributing/repo-branch.svg
    :alt: Branches

**Now it's time to make your changes**. Use the editor or IDE of your choice to do this.

4. Test if Your Changes Work
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

For SpongeAPI and the implementations you have to run ``gradle compileJava``. Proceed to the next step if it finishes
without errors. If it doesn't, make the appropriate corrections and try again.

For SpongeDocs you can just submit your PR. It will get built automatically and reveal possible errors. Another option
is to build the Docs locally. Have a look at the
`Readme.md on the Docs <https://github.com/SpongePowered/SpongeDocs/blob/master/README.md>`_ for further instructions.

5. Commit the Changes
~~~~~~~~~~~~~~~~~~~~~

When you're done, you need to bundle them into a single package (a ``commit``) and get them into the branch. Again your
git client will help you out. Add a meaningful name to your commit and a short description if needed. This can be done
via CLI too:

First collect all files and folders you want to put into a commit:

.. code-block:: none

  git add <file>
  git add <folder>

Now that the files are added to your list of changes you want included in the commit, just do

.. code-block:: none

  git commit

It will open a text window, where you can add a message if you desire. Have a look at the image below. You'll notice
that your commits are still stored locally only and not on your fork on Github.

.. note::
  You can have multiple commits in a PR. Just go ahead and change everything you need and commit the changes.
  You can merge the commits onto a single commit later.

So now, the sixth step is done. Almost there!

.. image:: /images/contributing/repo-commit.svg
    :alt: Committing

6. Sync to GitHub
~~~~~~~~~~~~~~~~~

Now we need to get the changes to your fork on GitHub. Everything you've made so far is only stored locally
right now. As always, you can use your git client to do this (there's a button somewhere in your GUI), or you can do
it via CLI:

.. code-block:: none

  git push <remote> <branch>

In this case it should be:

.. code-block:: none

 git push origin feature/YourFeature

.. image:: /images/contributing/repo-push.svg
    :alt: Pushing commits

7. Propose the Changes in a PR to the SpongePowered Repo
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You can either go to your forks page on GitHub.com (there should be a notice at the top of your forks page to
guide you), or you can use your GitHub client to create a pull-request. The official GitHub for Win client uses the
the top right corner of the window for this.

.. image:: /images/contributing/repo-pr.svg
    :alt: PRs

8. Amend Your PR if Necessary
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If we want you to make changes to your PR, then just make more commits to the branch created above.
Further commits will be added to your PR automatically.

9. Your PR Gets Pulled
~~~~~~~~~~~~~~~~~~~~~~

That's it. We're all set! Great job!

Advanced Git
============

Squashing with Rebase
~~~~~~~~~~~~~~~~~~~~~

Let's say you have finished your additions to the repo, and let's pretend that you made 137 commits while getting it done.
Your commit history will certainly look cluttered. It would be a shame if they were all recorded into the repo, wouldn't it?
Too many trivial commits also clutters the project commit history. Fortunately Git has a nice tool to circumvent this, it's
called a ``rebase``. Rebasing can take your 137 small commits and just turn them into one big commit. Awesome, isn't it?
Instead of reinventing the wheel, we'll just pass you a link to a very short and easily understandable squashing tutorial:

`Gitready: Squashing with Rebase <http://gitready.com/advanced/2009/02/10/squashing-commits-with-rebase.html>`_

This is what it does, nicely visualized:

.. image:: /images/contributing/repo-squash.svg
    :alt: Squashing commits

Setting Up a Remote
~~~~~~~~~~~~~~~~~~~

Naturally the original repo is the direct parent of your fork and your fork is the direct parent of your local clone.
However the original repo **isn't** the direct parent of your clone. This isn't a problem in the first place, but it
prevents you from updating your clone to the latest changes on the original repo. If you setup the original repo as a
remote (read: "parent") of your clone, you'll be able to grab all changes made to this repo and apply it to your local
clone. Look below to see how grabbing and updating works.

.. image:: /images/contributing/repo-remote.svg
    :alt: Setting up a remote

Alright. This step is done through CLI as most GUIs are missing this (rather advanced) functionality:

.. code-block:: none

 git remote add upstream https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git

If you're unsure if that worked as intended or if you want to check which remotes are currently set, you can check via:

.. code-block:: none

 git remote -v

the output should look like:

.. code-block:: none

 origin    https://github.com/YOUR_USERNAME/YOUR_FORK.git (fetch)
 origin    https://github.com/YOUR_USERNAME/YOUR_FORK.git (push)
 upstream  https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git (fetch)
 upstream  https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git (push)

.. note::
  If you see the warning ``fatal: The current branch YourBranchName has no upstream branch.``, then the branch may not be on
  the upstream remote. This may happen if this is the first time you are pushing a commit for the new branch. To push the
  current branch and set the remote as upstream, use ``git push --set-upstream origin YourBranchName``.

Rebasing
~~~~~~~~

Let's say you made some changes to your desired branch, but in the meantime someone else updated the repo. This
means that your fork and your clone are outdated. This is not a big problem, but to avoid problems when merging your
additions later on, it's strongly advised to ``rebase`` your changes against the latest changes on the original repo.
If you haven't set up the remote repo yet, do it before trying to rebase.

A successfull rebase requires several steps:

1. Fetch the Changes on the Remote Repo
---------------------------------------

First you need to fetch the changes on the remote repository. This is (again) done via CLI:

.. code-block:: none

 git fetch upstream

This will add all changes from the remote ``upstream`` and put them into a temporary ``upstream/master`` branch.

2. Merge Remote Changes locally
-------------------------------

Now we need to select our local ``master`` branch:

.. code-block:: none

 git checkout master

After that we'll merge the changes that are included in ``upstream/master`` into our local ``master`` branch:

.. code-block:: none

 git merge upstream/master

Alright, this is what we've done so far:

.. image:: /images/contributing/repo-rebase1.svg
  :alt: Rebasing 1

3. Rebase Local Branch against Updated Master
---------------------------------------------
Next up is rebasing the local branch you're working in against local ``master``. We need to switch to your working
branch (here: ``feature/yourfeature``) and then perform a rebase. This is done via:

.. code-block:: none

 git checkout feature/yourfeature
 git rebase master

This will rewind your branch, add the commits from master and then apply your own changes again. The result looks like
this:

.. image:: /images/contributing/repo-rebase2.svg
  :alt: Rebasing 2

4. Push Everything to your Fork
-------------------------------

The last thing we need to do is to push everything to the fork. If you've already created a PR, it will get updated
automatically:

.. code-block:: none

 git checkout master
 git push -f
 git checkout feature/yourfeature
 git push -f

.. image:: /images/contributing/repo-rebase3.svg
  :alt: Rebasing 3

You made it, awesome! Good job and well done and thanks for flying Rebase-Air!
