配合 BungeeCord 使用 Sponge
============================

BungeeCord 是由 md_5 和 SpigotMC 团队编写的一款服务器代理软件，允许服主把 Minecraft
服务器连接在一起，玩家无需断开重连就能在服务器之间进行切换。BungeeCord
通常被用在提供有多种游戏模式的服务器网络中。

有关 BungeeCord 是什么、如何设置它以及它是如何运作的更多信息，见
`BungeeCord 网站 <https://www.spigotmc.org/wiki/bungeecord/>`_。本页面将集中在 Sponge 的具体步骤上。

.. warning::
 为了将服务器连接到 BungeeCord，你必须以离线模式运行服务器。在离线模式下，如果没有适当的预防措
 施，任何人都可以使用他们想的任意名字登录到服务器，包括那些有管理权限的名字。确保你在使用防火墙来
 保护你的服务器。如果你正在使用
 Linux，`SpigotMC Firewall guide <https://www.spigotmc.org/wiki/firewall-guide/>`_ 上有一个
 IPTables 的指南，另外，某些发行版提供有
 `UncomplicatedFirewall "ufw" <https://wiki.ubuntu.com/UncomplicatedFirewall>`_。

如果你不习惯摆弄
Linux，或者你不确定如何防止非法访问到你的服务器，可考虑向更有经验的人咨询以确保你的服务器的安全。

.. note::

  如果你使用 SSH 请确保 22 端口是允许的，否则你真的在冒一个把你自己锁在你的服务器外面的险。

IP 转发
~~~~~~~~~~~~~

BungeeCord 有一个叫做 IP 转发的模式，允许 BungeeCord 将玩家的 UUID 和 IP
地址转发到任意已连接的服务器，甚至是以离线模式运行的服务器。当前 BungeeCord 构建的 IP 转发可与
SpongeVanilla 工作，同时只在原版客户端连接时支持 SpongeForge —— 当前版本的 BungeeCord
不能在需要模组客户端的模组服务器下原生使用 IP 转发。使用了修改版的 BungeeCord 或者社区提供的 BungeeCord
插件才能完全支持 SpongeForge。

允许 BungeeCord 原生支持 SpongeForge 的拉取请求已经提供给 BungeeCord。我们正在等待它被引入到主产品中：

* 旧 PR，上下文：`BungeeCord PR 1557 <https://github.com/SpigotMC/BungeeCord/pull/1557>`_
* 新 PR，为避免破坏使用了不同的方法：`BungeeCord PR 1678 <https://github.com/SpigotMC/BungeeCord/pull/1678>`_

使用没有 IP 转发的 BungeeCord
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

建议你尽可能地使用 IP 转发。如果你不希望使用，只需确保将你的 ``server.properties`` 文件中的 ``online-mode``
设置成 ``false`` 并且将服务器详情信息加到 Bungee 的 ``config.yml`` 文件中。在需要时 Bungee
会将任何的连接转发给服务器。一个好的预防措施是将 ``server-port`` 设置成 ``25565`` 之外的其它端口。

这与所有的 Sponge 实现都能工作，包括有模组的。

使用带有 IP 转发的 BungeeCord
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

如果你希望使用 IP 转发：

* 在 BungeeCord 的 ``config.yml`` 中，将 ``ip_forward`` 设置成 ``true``
* 在 Sponge 的配置中（config/global.conf），将 ``modules.bungeecord`` 和 ``bungeecord.ip-forwarding`` 设置成 ``true``
* 如果你有任何其它的服务器软件，请查阅该服务器的文档。

必须对 **所有** 连接到 BungeeCord 网络的服务器进行该操作。然后，只需按照使用没有
IP 转发的 BungeeCord 的说明操作即可。
