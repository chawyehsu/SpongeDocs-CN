========
命令
========

服务器管理员可以使用命令来管理他们的服务器，而玩家则可以通过命令与服务器进行交互。

在 Sponge 中，命令遵循权限系统。权限允许服务器管理员控制哪些人可以使用哪些命令。默认情况下会将所有命令授予给
OP 身份的玩家。没有管理员身份的玩家无法使用管理员命令或者那些需要分配权限节点的命令。服务器
管理员可以通过权限插件添加/取消权限节点来调整谁可以使用哪些命令。

.. note::

    Sponge 不是一个权限管理插件。要添加和取消个别玩家或组的权限，你需要找一个权限管理插件。

管理员命令
=================

这些命令，额外于普通玩家命令，对服务器管理员可用。

Sponge
~~~~~~

以下命令在由 Sponge 驱动的服务器中对具有管理员身份（或正确权限节点）的玩家可用。

====================  ========================================  ======================
命令                  描述                                      权限
====================  ========================================  ======================
/sponge audit         强制载入未载入的类以启用 Mixin 调试。     sponge.command.audit
/sponge chunks        打印世界、维度或全局的区块信息。          sponge.command.chunks
/sponge config        改变全局、世界或维度的配置。              sponge.command.config
/sponge heap          转储 JVM 堆。                             sponge.command.heap
/sponge plugins       列出当前已安装的插件。                    sponge.command.plugins
/sponge reload        重新载入全局、世界或维度的配置。          sponge.command.reload
/sponge save          保存全局、世界或维度的配置。              sponge.command.save
/sponge version       在控制台打印 Sponge/SpongeAPI 的版本。    sponge.command.version
/sponge timings       timings 模块的主命令。                    sponge.command.timings
====================  ========================================  ======================

|

**Sponge 命令参数**

* /sponge chunks [-g] [-d dim] [-w world]
* /sponge config [-g] [-d dim] [-w world] key value
* /sponge save [-g] [-d dim|*] [-w world|*]
* /sponge reload [-g] [-d dim|*] [-w world|*]

.. note::

    ``/sponge audit`` 命令强制载入所有未被载入的类，并允许采集 Mixin
    调试环境中所有变量的完整输出。这同时需要 mixins.checks 变量，更多信息见 `Mixin wiki
    <https://github.com/SpongePowered/Mixin/wiki/Mixin-Java-System-Properties>`__。

.. tip::

    这里是几个运行 sponge config 命令的简单示例。请查阅
    :doc:`../getting-started/configuration/index` 以获取更详细的解释。

    a. ``/sponge config logging.chunk-load true``

      由于未指定维度，默认将使用命令发送者（玩家）的维度。因此如果你在 mystcraft
      维度，这将会改变 mystcraft 维度的配置。

    b. ``/sponge config -d nether logging.chunk-load true``

    由于指定了维度，这将改变下界维度的配置（所有的下界世界）。

    c. ``/sponge config -w DIM1 logging.chunk-load true``

    这将改变名为 DIM1 的世界的配置。

Timings
~~~~~~~

Timings 是一个内置在 Sponge 中的工具，允许服务器管理员监视他们的服务器的性能。Timings
将收集有关服务器的信息以在后续基于这些数据生成一份报告。由 Timings 记录的信息包括服务器的
motd、版本、在线时间、内存、安装的插件、tps、tps 丢失百分比，玩家数量、tile
entities、实体以及区块。以下是 ``/sponge timings`` 的子命令列表：

========================  ========================================
命令                      描述
========================  ========================================
/sponge timings on        启用 Timings。注意这将同时重置 Timings
                          数据。
/sponge timings off       禁用 Timings。注意 Timings 禁用后大部分
                          Timings 命令将无法使用同时 Timings
                          将不会进行记录工作。
/sponge timings reset     重置所有 Timings
                          数据并在此命令结束后开始记录 Timings 数据。
/sponge timings report    在 http://timings.aikar.co
                          上生成你的服务器性能 Timings 报告。
/sponge timings verbon    启用详细信息级别的 Timings 监控。
/sponge timings verboff   禁用详细信息级别的 Timings
                          监控。注意高频 Timings 将不可用。
/sponge timings cost      获取使用 Timings 时的消耗。
========================  ========================================

Forge
~~~~~

以下命令只有在 Forge 中使用了 SpongeForge coremod
才可用。Sponge API 的其它实现，如 SpongeVanilla，不包含这些命令。

====================  ========================================  ====================
命令                  描述                                      权限
====================  ========================================  ====================
/forge tps            显示每个世界的 TPS。                      forge.command.forge
/forge track          开启 Tile Entity 跟踪。                   forge.command.forge
====================  ========================================  ====================

|

为了让所有的 Forge 模组可以使用原版命令 API，命令权限以 ``<modid>.command.<commandname>`` 的形式提供。


原版
~~~~~~~

原版 Minecraft 中内建的一些命令在由 Sponge 驱动的服务器中也可用。以下列表并不全面，但包含了最常用的命
令。这些命令对有管理员身份（或正确权限节点）的玩家可用。一般情况下，Sponge 服务器中的原版 Minecraft
命令权限的结构是 ``minecraft.command.<command>``，如下所示。

====================  ========================================  ================================
命令                  描述                                      权限
====================  ========================================  ================================
/ban                  封禁玩家。                                minecraft.command.ban
/ban-ip               封禁玩家的 IP 地址。                      minecraft.command.ban-ip
/banlist              查看所有被封禁的玩家。                    minecraft.command.banlist
/clear                清空背包。                                minecraft.command.clear
/deop                 移除玩家的 OP 身份。                      minecraft.command.deop
/difficulty           设置游戏难度。                            minecraft.command.difficulty
/gamemode             设置玩家的游戏模式。                      minecraft.command.gamemode
/gamerule             设置游戏规则。                            minecraft.command.gamerule
/give                 给予玩家物品。                            minecraft.command.give
/kill                 杀死玩家或实体。                          minecraft.command.kill
/op                   给予玩家管理员身份。                      minecraft.command.op
/pardon               将玩家从封禁列表中移除。                  minecraft.command.pardon
/save-all             存档服务器。                              minecraft.command.save-all
/save-off             禁用服务器自动存档。                      minecraft.command.save-off
/save-on              启用服务器自动存档。                      minecraft.command.save-on
/setidletimeout       定义玩家空闲多少 tick 后被踢出。          minecraft.command.setidletimeout
/setworldspawn        设置世界的出生点。                        minecraft.command.setworldspawn
/stop                 关闭服务器。                              minecraft.command.stop
/toggledownfall       切换晴天和雨天。                          minecraft.command.toggledownfall
/tp                   传送玩家或实体。                          minecraft.command.tp
/weather              定义条件设置天气。                        minecraft.command.weather
/whitelist            管理服务器白名单。                        minecraft.command.whitelist
/worldborder          管理世界边境。                            minecraft.command.worldborder
====================  ========================================  ================================

|

此外，Sponge 创建了两个用于控制编辑命令方块能力的权限。注意该权限使用命令方块的实际 *名字*，默认是 ``@``。

* 允许编辑给定名字的普通的命令方块：minecraft.commandblock.edit.block.<name>
* 允许编辑给定名字的命令方块矿车：minecraft.commandblock.edit.minecart.<name>


玩家命令
===============

以下是原版 Minecraft 的部分命令，对没有管理员身份的玩家可用。

====================  ========================================  ======================
命令                  描述                                      权限
====================  ========================================  ======================
/help                 查看服务器内可用命令的信息                minecraft.command.help
/me                   告诉所有人你在正在做什么。                minecraft.command.me
/say                  向所有人显示一条消息。（如使用了选择器，  minecraft.command.say
                      则指定玩家）。
/tell                 向其他玩家发送私密消息。                  minecraft.command.tell
====================  ========================================  ======================

|

原版命令的完整列表可以在这里找到：http://minecraft.gamepedia.com/Commands#List_of_commands。在 Sponge
服务器中原版 Minecraft 命令权限的结构是 ``minecraft.command.<command>``。
