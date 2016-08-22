==============
安装 Git
==============

Git 是一个开源的版本控制系统，它极大地帮助了项目的协同开发。

Sponge 项目与其它数以千计的开源项目一样，将它的代码托管在了 GitHub 上。因此，Git
是 Sponge 及 Sponge API 开发中至关重要的工具。

`Git 网站 <https://www.git-scm.com/>`__ 上有大量的文档，同时它们的下载页面提供一系列适用于各种操作系统的 GUI 客户端。

下载
========

Windows
~~~~~~~

`GitHub Desktop <https://desktop.github.com/>`_ 是一种在 Windows 上安装 Git 的简易方式，因为 Git 已集成在该软件中。

建议在安装完成后重启你的计算机。

Mac
~~~

在 Mac OS X 上安装 Git 有多种方式。

最简单的方法是安装 Xcode Command Line Tools。

.. warning::

    以下指令不适用于比 Mavericks 更旧版本的系统。如果你正在使用一个比 Mavericks
    更旧版本的 OS X 系统，请安装 Github Client。

1. 启动终端。
#. 执行 ``xcode-select --install``。
#. 等待安装，也许你可以乘机来块饼干。
#. 在终端运行 ``git``。

或者，你可以安装 `GitHub Desktop <https://desktop.github.com/>`_。安装 GitHub Desktop 后 Git 部分也是可用的。

建议在安装完成后重启你的计算机。

Linux and Unix
~~~~~~~~~~~~~~

在 Linux 上安装 Git 最简单的方法是使用你的发行版的包管理系统。

.. note::

    你也许需要在以下命令前加上 ``sudo``。

1. 启动终端。
#. 如果你使用 Ubuntu 之类的 Debian 系发行版，执行 ``apt-get install git``。如果是 Fedora，执行 ``yun install git``。

不像 Windows 和 Mac，GitHub Desktop 目前没有 Linux 版。

建议在安装完成后重启你的计算机。

设置
=====

你是谁？
~~~~~~~~~~~~

在开始使用 git 和仓库之前，请确保你的 git 配置已设置了你的身份。打开你的 CLI 并输入：

.. code-block:: none

   git config --list

查找 ``user.name`` 和 ``user.email``。如果它们和你在 GitHub 帐户上的用户名和电子邮件不同，请设置它们：

.. code-block:: none

   git config --global user.name "John Doe"
   git config --global user.email johndoe@example.com


.. tip::

   在确立你的 ``user.name`` 和 ``user.email`` 之前，不要对 Sponge 的任意仓库做出任何提交。
