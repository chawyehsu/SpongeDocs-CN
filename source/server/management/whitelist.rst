======================
白名单管理
======================

白名单机制允许你控制谁可以加入你的服务器。请注意 OP *总是* 可以加入服务器的，不管他们在不在白名单中。


当白名单功能被启用时，只有那些名字在白名单中的玩家可以加入服务器。可以通过游戏内指令或直接编辑 ``whitelist.json``
文件来将玩家添加到白名单中。但请注意：如果你手工修改文件，则必须重新载入白名单或是重
启服务器来让修改生效。此外，请特别注意语法的正确性，否则白名单将不工作。一个格式正确的白名单文件样例
可以在这里找到 :doc:`../../server/getting-started/configuration/json`。

- 要启用白名单，请使用 ``/whitelist on``
- 要禁用白名单，请使用 ``/whitelist off``
- 要添加一位玩家到白名单，请使用 ``/whitelist add playername``
- 要从白名单中移除一位玩家，请使用 ``/whitelist remove playername``
- 要列出白名单中的所有玩家，请使用 ``/whitelist list``
- 要在手工修改文件后重新载入白名单，请使用 ``/whitelist reload``

白名单也可以在 :doc:`../../server/getting-started/configuration/server-properties`
文件中被启用或禁用，但这需要重启服务器才会生效。
