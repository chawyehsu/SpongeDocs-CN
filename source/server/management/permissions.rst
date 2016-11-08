====================
权限管理
====================

你可以通过使用权限来配置谁有权限访问你正在运行的服务器。在 :doc:`../../server/spongineer/commands`
页面中展示有 Sponge，Forge 以及 Minecraft 的特有权限指令。


管理员级别
==============

Minecraft 自带简单的权限管理方法：将用户设置为管理员（或简称
``op``）。op 状态的有关信息可以在这里找到 http://minecraft.gamepedia.com/Op

op 权限的能力可以通过修改 :doc:`../../server/getting-started/configuration/server-properties`
文件中的 ``op-permission-level`` 设置来进行调整。

Minecraft 服务器原生的 op 指令列表可以在 `Minecraft Wiki
<http://minecraft.gamepedia.com/Commands#Summary_of_commands>`_ 上找到。


.. warning::
   Minecraft 只有 op，没有任何细粒度的权限管理能力。op
   的权限等级非常高，应赋予信任的玩家。更多复杂权限设定需要使用权限插件或者模组。Sponge 
   不是一个权限管理插件。


.. note::
   某些插件与模组可能会赋予 op 一些特定的权限。
