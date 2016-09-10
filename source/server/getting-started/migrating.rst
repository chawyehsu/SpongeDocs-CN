===================
迁移到 Sponge
===================

本文内容旨在帮助服主将服务器从其它平台迁移到 Sponge。

.. only:: html

.. contents::
   :depth: 2
   :local:

.. warning::
  请在进行迁移 **之前** 备份你的服务器文件。万一出现问题，你还有你的备份！

迁移到 Sponge
===================

下面的章节将帮助你迁移至 SpongeForge 或 SpongeVanilla。大部分指令是通用的，若有不同会有说明。

从 CraftBukkit 或 Spigot 迁移
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. note::

    Spigot 是 CraftBukkit 的一个派生修改版本。

世界存档
--------

Forge 与 SpongeForge（还有 SpongeVanilla）跟原版 Minecraft 使用相同的世界存档结构。原版 Minecraft
将地狱（通常是 ``world_nether``）和末地（通常是 ``world_the_end``）维度保存在 ``world`` 文件夹里。而
Bukkit 与 Spigot 却 *不* 使用这种世界存档机制，因此需要进行迁移。

SpongeForge 与 SpongeVanilla 提供了一个帮助你转换世界存档的全自动转换脚本。以下是工作流程：

1. 关闭你的 Bukkit 或 Spigot 服务器并备份整个文件夹。

#. 将 SpongeForge 或 SpongeVanilla 安装到你运行旧有服务器的文件夹中，同时删除 Bukkit 或 Spigot 的
   jar。如果你不确定如何正确地安装 SpongeForge 或 SpongeVanilla，请查阅 :doc:`这篇文章 <implementations/index>`。

#. 启动 Sponge 服务器，迁移脚本将会自动载入。

#. 迁移脚本会在 ``bukkit.yml`` 中查找一个叫做 ``world-container``
   的配置键并搜索待转换的世界存档的文件夹。如果该文件不存在（或因某些原因导致它不可读），则迁移脚本会使用服务器的
   ``根`` 目录（即 CraftBukkit 的顶层文件夹）。

#. 现在迁移已在执行。这时，世界存档会从我们说的 ``world container``，复制到在
   :doc:`configuration/server-properties` 文件中 ``level-name`` 键定义的文件夹中。注意迁移过程中只是 *复制*
   了一份世界存档，没有修改 ``world container`` 中的原文件。

#. Bukkit 将文件（以奇怪的名字）放在了奇怪的位置，因此要进行两个重要的修正。不过请记住以下修正是
   *设想* 的（根据 Bukkit 的结构）。

   * 第一个修正是将所有以 ``level-name`` 属性开头并以原版的维度名称（即
     ``_nether``/``_the_end``）结尾的文件夹分别重命名成 ``DIM-1`` 和 ``DIM1``。

   * 第二个修正是迁移 Bukkit 的 nether/the_end 中的 ``region`` 数据。Bukkit 将这些数据分别放在了
     ``DIM-1\region`` 和 ``DIM1\region`` 中，而原版 / Forge 则要求 ``region``
     要在世界存档文件夹的 **根** 目录中。

迁移脚本不能设置所有必需的配置值。这就是为什么你需要手动更改部分参数来使世界存档在
SpongeForge 或 SpongeVanilla 中正常地载入工作。强烈建议使用 *世界管理插件* 来正确地设置参数和加载世界存档。

.. note::
  在迁移世界存档时我们必须要处理如前所述的几个设想。**因此
  Sponge 不会直接加载世界存档**，对此你需要安装插件来解决。

如果一切顺利的话，迁移脚本工具生成的输出应该如下所示：

.. code-block:: none

 [17:32:29] [Server thread/INFO] [Sponge]: Checking for worlds that need to be migrated...
 [17:32:29] [Server thread/INFO] [Sponge]: Migrating [world_lol] from [.].
 [17:32:29] [Server thread/INFO] [Sponge]: Migrated world [world_lol] from [.] to [.\world\world_lol]
 [17:32:29] [Server thread/INFO] [Sponge]: Migrating [world_nether] from [.].
 [17:32:29] [Server thread/INFO] [Sponge]: Migrated world [world_nether] from [.] to [.\world\DIM-1]
 [17:32:29] [Server thread/INFO] [Sponge]: Migrating [world_the_end] from [.].
 [17:32:29] [Server thread/INFO] [Sponge]: Migrated world [world_the_end] from [.] to [.\world\DIM1]
 [17:32:29] [Server thread/INFO] [Sponge]: [3] worlds have been migrated back to Vanilla's format.

完成后，你应该会得到一份结构上能被 Sponge 加载的世界存档副本。以防万一出错，原始的世界存档文件保留在其原位置。

服务器与世界存档配置文件
------------------------------------

CraftBukkit 和 Sponge 都会使用原版 Minecraft 生成的配置文件。因此在
CraftBukkit 服务器文件夹中的以下文件可以被直接使用到 Sponge 服务器中：

* ``server.properties``
* ``banned-ips.json``
* ``banned-players.json``
* ``ops.json``
* ``usercache.json``
* ``whitelist.json``

以下文件只被 CraftBukkit 使用，而 Sponge 服务器不需要使用，可以删除：

* ``bukkit.yml``
* ``commands.yml``
* ``help.yml``
* ``permissions.yml``

从 Spigot 进行迁移的用户可以拿 ``spigot.yml`` 和 Sponge 中的 ``global.conf`` 作对比。``spigot.yml``
中的一些键在 ``global.conf`` 中有对应，并且可以复制使用在两个文件中都出现的键值。

插件
-------

Sponge 不能原生支持 Bukkit 插件。但是，一些社区开发者正在制作一个特别的 Sponge 插件来重新实现
Bukkit API，这使得一些 Bukkit 插件运行于 Sponge 服务器上成为可能。这个插件目前还没有正式发布。

Ore 是 Sponge 的官方插件仓库，建议从 Ore 上下载所有的 Sponge
插件。而在为你的 Bukkit 插件寻找替代时，有几点需要注意：

* 不是所有的 Bukkit 插件开发者都会选择将他们的插件移植到
  Sponge 上。不过，随着时间的推移，或许会有一些人制作出合适的替代品。
* 不是所有从 Bukkit 移植到 Sponge
  上的插件都会自动转换配置文件。这取决于独立插件开发者是否有做配置文件自动转换的决定。
* 一些从 Bukkit 移植过来的 Sponge 插件在功能上可能会有所差异，或有可能使用了不同的配置文件结构。

从 Canary 迁移
~~~~~~~~~~~~~~~~~~~~~

世界存档
--------

Forge 与 SpongeForge（还有 SpongeVanilla）跟原版 Minecraft 使用相同的世界存档结构。原版 Minecraft
将地狱（通常是 ``world_nether``）和末地（通常是 ``world_the_end``）维度保存在 ``world`` 文件夹里。

Canary 将地狱和末地维度迁移到了 ``world`` 文件夹之外，如果想在运行
Sponge 时保留地狱和末地维度的话请务必注意这一点。不过，Canary 提供了一个易用的方法，通过使用 ``/makevanilla``
指令便可将 Canary 的世界存档转换为能被 Sponge 使用的结构。成功转换后的世界存档会保存在 ``vanilla`` 文件夹里。

服务器与世界存档配置文件
------------------------------------

Sponge 会使用许多由原版 Minecraft 提供的文件，比如 ``server.properties``。Canary 则不同，它与原版 Minecraft
共有的只有 ``usercache.json`` 文件。所以，Canary 中能被 Sponge 重新使用的就只有 ``usercache.json`` 文件。

尽管如此，还是能够手动将一些 Canary 配置文件对应地迁移到 Sponge 中，具体如下：

+----------------------------+----------------------------+
| Canary 文件                | 对应的 Sponge 文件         |
+============================+============================+
| server.cfg                 | server.properties          |
| <world>_<dimension>.cfg    |                            |
+----------------------------+----------------------------+
| <world>_<dimension>.cfg    | global.conf                |
|                            | <dimension>/dimension.conf |
+----------------------------+----------------------------+
| ops.cfg                    | ops.json                   |
+----------------------------+----------------------------+
| db.cfg                     | 无对应文件                 |
+----------------------------+----------------------------+
| motd.txt                   | 无对应文件                 |
+----------------------------+----------------------------+

插件
-------

SpongeVanilla 和 SpongeForge 不能原生支持 Canary
插件。可能会有一个特别的 Sponge 插件来重新实现 Canary API。

Ore 是 Sponge 的官方插件仓库，建议从 Ore 上下载所有的 Sponge
插件。而在为你的 Canary 插件寻找替代时，有几点需要注意：

* 不是所有的 Canary 开发者都会选择将他们的插件移植到 Sponge
  上。不过，随着时间的推移，或许会有一些人制作出合适的替代品。
* 不是所有从 Canary 移植到 Sponge
  上的插件都会自动转换配置文件。这取决于独立插件开发者是否有做配置文件自动转换的决定。
* 一些从 Canary 移植过来的 Sponge 插件在功能上可能会有所差异，或有可能使用了不同的配置文件结构。
 

从 Forge 迁移
~~~~~~~~~~~~~~~~~~~~

从一个普通的 Forge 服务器迁移到 SpongeForge 或 SpongeVanilla
服务器是一个相当简单的过程，只需要非常少的筹备工作。

迁移到 SpongeForge
------------------------

你必须先确保你正在使用的 Forge 版本兼容你打算使用的 SpongeForge 版本。你可以在
`Forge 下载 <http://files.minecraftforge.net>`_ 上找到推荐的 Forge
构建。如果你有使用任何其它模组，务必同时升级它们。

在准备好安装 SpongeForge 时，你可以继续执行以下步骤：

1. 停止你正在运行的 Forge 服务器。
#. 从 Sponge 和 MinecraftForge 网站上下载 SpongeForge 与 Forge。
#. 将 ``SpongeForge.jar`` 放进你的 ``mods`` 文件夹中。
#. 可以开服玩耍了！

.. note::

    如果 SpongeForge
    是你服务器里唯一的一个模组，则玩家可以使用原版客户端登录。其它模组则要求玩家在他们的计算机中安装 Forge。

迁移到 SpongeVanilla
--------------------------

.. warning::

    如果迁移到 **SpongeVanilla**：你将会失去所有的 Forge
    模组数据、方块以及实体，因为 SpongeVanilla 不能运行 Forge 模组。
    在你决定要迁移到 SpongeForge 还是 SpongeVanilla 时请记住这一点。

迁移过程几乎与上面的一样：

1. 停止你还在运行的 Forge 服务器。
#. 下载 SpongeVanilla 并从 Mojang 下载原版服务器。
#. 将你的世界存档和配置文件放到服务器文件夹中。
#. 通过启动 ``spongevanilla.jar`` 运行服务器。


从原版（Vanilla）迁移
~~~~~~~~~~~~~~~~~~~~~~

原版 Minecraft 服务器的管理员可以容易地迁移到 Sponge，因为 Forge 和 SpongeForge（以及
SpongeVanilla）都使用与原版服务器相同的世界存档结构。同时 Sponge 还使用与原版 Minecraft
服务器相同的配置文件，比如 ``server.properties``。

首先你应该决定你想运行 SpongeForge 还是 SpongeVanilla。

.. note::
    “两种口味的海绵”都能服务原版客户端。请记住这只在你没有安装需要修改客户端的模组时才对 SpongeForge 适用。

1. 停止你还在运行的原版服务器。
#. 下载 SpongeVanilla 或者 SpongeForge。
#. 将你的世界存档和配置文件放到服务器文件夹中。
#. 运行你的新服务器。

安装 Sponge
=================

在进行迁移时，可以查阅在 :doc:`implementations/spongeforge` 和
:doc:`implementations/spongevanilla` 提供的 Sponge 安装说明指南。
