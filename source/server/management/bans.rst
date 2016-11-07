=============
封禁管理
=============

Minecraft 有一套简易的封禁管理来阻止意图不良的用户加入你的服务器，因此 Sponge 也有。


``/ban <name> [reason]`` 指令是 Minecraft 服务器的一个原生功能，可封禁名为 *name*
的玩家。使用 ``/banlist players`` 指令可查看完整的封禁玩家列表。

也可以使用 ``/banip <address|name> [reason]`` 指令封禁给定 IP
上的所有连接。使用 ``/banlist ips`` 指令可查看完整的 IP 封禁列表。

可以使用 ``/pardon <name>`` 或 ``/pardon <ip-address>`` 指令解除封禁。


更多关于封禁的信息可以在 `Minecraft Wiki <http://minecraft.gamepedia.com/Commands#ban>`_ 上找到。
