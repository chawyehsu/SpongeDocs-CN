==================
配置 Sponge
==================

你可以在 "config" 文件夹下找到所有的配置文件。

配置语法
=============

大多数配置文件使用 :doc:`HOCON <hocon>` 格式。

.. toctree::
    :maxdepth: 3
    :titlesonly:

    hocon
    json

你可以配置什么
======================

.. toctree::
    :maxdepth: 3
    :titlesonly:

    sponge-conf
    server-properties

插件会在 "config" 文件夹内有其自己的配置文件。

世界配置
=============

有三种类型的世界配置：

* 全局
* 维度
* 世界

全局配置文件可以影响所有服务器的世界和维度。这是默认的配置级别。维度配置文件用于影响某个具体的维度或
者世界组。这些类型的配置会覆盖全局配置文件。世界配置文件用于修改单独的世界。世界配置会覆盖全局配置和维度配置。

在游戏中修改配置
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

可以通过使用游戏中的 ``/sponge config`` 指令修改这些配置。配置指令的语法看起来像这样：

.. code-block:: java

    /sponge config <flag> <key> <value>

*标志* （flag）用于指定你想要修改的目标。标志有全局、维度和世界。

* ``-g`` 是全局的标志
* ``-d <dim>`` 标记一个维度（把 *<dim>* 替换成你想要配置的维度）
* ``-w <world>`` 标记一个世界（把 *<world>* 替换成你选择的世界）。

*key* 是你想要更改的值。*value* 则是你想要把 key 对应的值改成什么样子。

这里是一个运行该指令的例子：

.. code-block:: java

    /sponge config -d nether logging.chunk-load true

这将会设置为当下界的区块被加载时进行日志记录。

如果你需要检查一个键对应的值，则需要省略 *value*。检查下界中 ``logging.chunk-load`` 对应的值可以像这样做：

.. code-block:: java

    /sponge config -d nether logging.chunk-load

保存世界配置
~~~~~~~~~~~~~~~~~~~~~

在完成修改后可能希望把世界配置保存到文件中。在服务端发生意外崩溃事件时这会很有用。在 Sponge
服务器中可以使用 ``/sponge save`` 指令保存配置。该指令的语法与配置指令相似：

.. code-block:: java

    /sponge save <flag>

以下是一个保存全局配置的示例：

.. code-block:: java

    /sponge save -g

重新载入世界配置
~~~~~~~~~~~~~~~~~~~~~~~~

有时候可能希望在服务器仍在运行之时重新载入世界配置。在你修改了本地配置文件并想在正在运行的服务器中重
新载入使用时这会很有用。可以通过使用 ``/sponge reload`` 指令完成这件事，下面是该指令的语法：

.. code-block:: java

    /sponge reload <flag>

以下是一个重新载入末地配置文件的示例：

.. code-block:: java

    /sponge reload -d the_end
