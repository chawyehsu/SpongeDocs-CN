=========================
提交拉取请求
=========================

基础
==========

首先你需要设置你的机器能够进行 Sponge 开发：

* 查阅 :doc:`/preparing/index` 并设置你的机器
* 熟悉 git 和 GitHub：:doc:`../howtogit`
* 阅读我们的 :doc:`代码规范 <codestyle>` 和 :doc:`../guidelines`
* 熟悉我们的 :doc:`git-implementation`

当你完成并认为你已经做好 Sponge 开发的准备时，决定你想参与哪个部分的工作。

PR 的编写
============

修复漏洞
~~~~~~~~~~~

用几句话解释：

* 你遇到的漏洞，尤其是

  * 它的表现
  * 你认为它应该如何表现

* 你修复了什么
* 你怎么修复的

API 的重大增补
~~~~~~~~~~~~~~~~~~

你已经开发了相当重大的 API 增补并想提交 PR。这很好！建设性的 PR 会让这个项目变得更好。这也要我们去书写美妙的 PR 描述。

过去有一些在标准之上，超越了标准的例子，如：

* `Inventory API PR <https://github.com/SpongePowered/SpongeAPI/pull/443>`_
* `Data API PR <https://github.com/SpongePowered/SpongeAPI/pull/542>`_

当然，上述是一些极端例子，以下是一些已被接受的 PR，它们可以作为在 PR 描述中应该包含什么内容的一个好的标准：

* `Event Filtering PR <https://github.com/SpongePowered/SpongeAPI/pull/927>`_
* `Bans improvement API PR <https://github.com/SpongePowered/SpongeAPI/pull/954>`_

从以上例子中可以采用到的几个点：

* 在 PR 的开头清楚地给出任何其它实现的 PR 的链接，这个可以用 GitHub 的 Markdown 做到。

.. code-block:: none

  *SpongeAPI*|[SpongeCommon](html link)|[SpongeForge](html link)|[SpongeVanilla](html link)


* 对 API PR 的目的作一个清楚的描述，根据其功能写一个简短的概括，就好像写一篇短文，至多 4 个句子。

* 举出插件如何能使用这个新特性的代码示例（如果已经存在旧特性，说明为什么要更改它们）。
