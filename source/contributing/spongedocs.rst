==================
SpongeDocs 的编写
==================

Sponge 文档，也被称为“SpongeDocs”，是 Sponge 项目的官方文档。SpongeDocs 的目标是：

* 帮助用户建立他们自己的由 Sponge 的实现驱动的服务器。
* 为开发者提供有关如何向 Sponge 项目做贡献的信息。
* 为开发者提供有关如何开始进行插件开发的信息。


问题反馈
==================

总会有可能一个页面出现过时、错误，或者当你看着一个页面时想过“嗯，这里能有更好的方式来说明”的情况。
如果是这样，而你又出于某种原因不能亲手提供修正时，这里有三种方式能让我们意识到这些问题：

#. 在 `SpongeDocs GitHub 上开 issue <https://github.com/SpongePowered/SpongeDocs/issues>`_
#. 在 `论坛的 SpongeDocs 分类 <https://forums.spongepowered.org/c/sponge-docs>`_ 发帖
#. 访问我们在 `irc.esper.net 上的 #spongedocs 频道 <irc://irc.esper.net:6667/spongedocs>`_ （需要注册）

编写文档
================

对 SpongeDocs 的增加与更改应该以向 `SpongeDocs 的 GitHub 仓库 <https://github.com/SpongePowered/SpongeDocs>`_
提交拉取请求进行。我们不要求拉取请求一开
始就很完美，因为在评审阶段进行改良是很常见的事。我们也欢迎未完成的说明，所以如果其中有你不懂的地方请
不要害怕。总是会有人能够去填补空白的。

我们使用 reStructuredText（reST） 来编写文档，如果你熟悉 Markdown（md）的话那么 reST
对你不应是难事。如果你对此有疑问，我们建议你加入我们的 `论坛 <https://forums.spongepowered.org/>`_
或者 Esper.net 上的 `#SpongeDocs 频道 <irc://irc.esper.net:6667/spongedocs>`_ 获取帮助。

风格指南
===========

为了确保我们所有的 SpongeDocs 页面具有一致的格式，这里我们制定了一套关于编写 Sponge
文档的指南。这份列表可能会随着文档的变大而进行增加（或改变）。

1. 标题书写应该首字母大写（除非第 8 点生效）
2. 页面标题应该有意义（带有超链接的标题）
3. 程序代码应该使用 `内联文本 <http://docutils.sourceforge.net/docs/ref/rst/roles.html#literal>`__ 或者代码块。

  i. 尽量不要往代码块中放入太多的文本，因为它们不能被翻译。任何情况下我们都不主张贡献者在
     代码块中编写注释。某些情况下可能有必要使用简单的占位符文本。理想情况下，代码块例子要
     简短，并且在正文中为每个例子附上说明。诚然，有些概念不能使用简短的例子来说明。

4. 为用户、插件开发者以及 Sponge 开发者保留各自独立的区域。
5. 在可能的地方共用页面，避免重复。
6. 对于外部资源使用链接而不是复制一份。

  i. 对于翻译目的可以有例外情况。

7. 区分 SpongeForge，SpongeVanilla 与 SpongeAPI。
8. 如果这在你的语言中看起来很糟糕，制定你自己的规则。
9. Sponge 是这个项目的标题，不应该被翻译。

  i. 也可能某些语言希望使用音译。

10. 强烈不推荐使用机器翻译（例如 Google 翻译）。机翻往往包含严重错误，还很有可能被拒绝。
11. 页面标题与章节标题应该使用纯文本，避免使用块级文本等其它格式。
12. 代码符号应该保留它们原有的大写格式，且没有额外的空格（例如 blockState（一个字段名）或者
    BlockState（一个类名），而不是
    *block state*）。同时在正文中代码符号应该使用反撇号格式化成内联块级文本（例如 ``blockState``）。
13. 一行的长度应该最多 120 个字符。
14. 有多篇文章引用的代码块中，若有引入（import），应该仅在第一篇文章中引入一次，后续不再引入。


.. Note::

    正如 Sponge 仍在不断变化，开发文档的短缺是意料之中的。毫无疑问，在
    Sponge 推出正式版之前，文档仍有许多空缺点。然而，SpongeDocs
    是一个时刻在被编辑的活文档。它不完美，只会被打磨成所需的形状。

*随时欢迎贡献、建议以及纠正。*
