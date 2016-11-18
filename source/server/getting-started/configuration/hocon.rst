=====================
HOCON 简介
=====================

HOCON（Human-Optimized Config Object Notation）是一个易于使用的配置格式。Sponge 以及利用了
Sponge API 的独立插件使用它来储存重要的数据，比如配置或者玩家数据。HOCON 文件通常使用 ``.conf`` 后缀。

组件
===========

* ``key`` 是 value 前面的一个字符串
* ``value`` 是 ``key`` 后面的一个字符串、数字、对象、数组或者布尔值
* ``key-value separator`` 把 key 和 value 分开，可以是 ``:`` 或者 ``=``
* ``comment`` 以 ``#`` 或者 ``//`` 开头，通常用于提供反馈或者说明

**示例：**

.. code-block:: json

      yellow-thing: "Sponge"

在这一示例中， ``key`` 是 ``yellow-thing``，``value`` 是 ``Sponge``，而 ``key-value separator`` 则是 ``:``。

使用 HOCON
==================

HOCON 比 JSON（JavaScript Object Notation）格式更灵活，书写一个合法的
HOCON 有多种方式。下面是两个合法的 HOCON 示例。

**示例一：**

.. code-block:: none

    player: {
        name: "Steve",
        level: 30
    }

**示例二：**

.. code-block:: none

    player {
        name = "Steve"
        level = 30
    }

在实际使用中，最好遵守你正在编辑的 HOCON 配置的格式约定。在编辑 Sponge 或者利用了 Sponge API
的独立插件的 HOCON 配置文件时，你可能修改的应只有 value，除非另有指定。

调试你的配置
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

如果一个 HOCON 配置文件似乎不工作，这里有一些小提示。

* 必须匹配花括号
* 必须引号匹配
* 重复的键后一个优先

规范
=============

在 `这里 <https://github.com/typesafehub/config/blob/master/HOCON.md>`__ 可以找到有关 HOCON 格式的更多信息。
