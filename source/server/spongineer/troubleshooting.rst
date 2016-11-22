===============
故障排查
===============

你会来到这里可能是因为你的 Sponge 服务器出了某些毛病。让我们看看我们是否能找出病因并对症下药吧。

.. contents:: **可能的故障来源**
   :depth: 2
   :local:


你的计算机上没有安装 Java
--------------------------------------

**解决方案**: 安装 Java。请查阅 :doc:`../../server/getting-started/jre` 获取更多信息。

网络连接失败（或 DDoS 攻击）
-------------------------------------------

**症状**：网络连接延迟大，丢包，或无法连接。

**解决方案**：检查你的调制解调器或路由器的连接。查看你的浏览器是否有相似的问题。可以使用如 speedtest.net
等免费服务检查你的连接速度。可能是由运行在你的计算机或本地网络中的其它服务造成的。确保你在你的路由器
上启用了端口转发。DDoS 攻击可能会让你的连接完全瘫痪，虽然这不太可能，但如果你相信是这个导致的，你应该联系你的 ISP。

没有足够的可用内存
----------------------

**症状**：服务器崩溃，往往伴随着 ``内存不足`` 的消息。

**解决方案**：使用 ``-XX:MaxPermSize=128`` 启动参数扩大非堆内存的最大尺寸。（如果可行）使用启动参数如
``-Xms1024M`` （1GB 启动内存）和 ``-Xmx2048M``
（最大 2GB）扩大你的服务器的堆内存。监控你的计算机上的可用内存并查看是否有其它进程被锁。你可能需要杀掉冻结的
java 进程，或者重启你的机器。插件的 BUG 有时候会造成内存泄漏，这需要花些时间进行隔离。

**仍然有问题？**：尽管尝试了上述情况但还是有问题而又不能增加堆内存，可检查你的任务管理器看看你是否用光了
所有的可用内存。如果是，那唯一的解决方案是给你的系统增加内存。如果还有大量的可用内存，那就是你正在使用 32 位的
Java。如果你正在使用 32 位的 Java，你的操作系统是 64 位的，我们建议升级到 64 位的 Java。

配置文件格式不正确（例如：拼写错误）
---------------------------------------

**症状**：一个（或多个）插件拒绝载入，或者以非预期方式运行。服务器日志文件会包含有关在启动时无法读取的文
件的消息。服务器可能崩溃，以及数据可能损坏了。

**解决方案**：关闭服务器，并检查你编辑过的文件。加载损坏数据的备份文件。你可能需要完全删除配置文件并让它
在服务器启动时重新生成。

插件（或模组）出现故障
-----------------------------------

**症状**：这可能会发生任何情况——取决于你使用的插件，还可能有未知的因素。通常在服务器崩溃时服务器日志文
件中会带有一长串的错误消息。

**解决方案**：Stop the server, and check to see nothing has been corrupted. Be sure to check that it isn't from an
incorrectly edited config file (above). Remove suspect plugins and add them again one by one, restarting the server
each time. The problem may originate from one plugin that is out of date - check for updates. Plugin conflict may also
be the cause, having two incompatible plugins.

操作系统不稳定（如感染病毒）
--------------------------------------------------

**症状**：The server keeps crashing or timing out, and other parts of your operating system are also having problems.

**解决方案**：Stop everything. Thoroughly check your system and storage devices for malware and viruses. Good tools
for this include AdwCleaner, Junkware Removal Tool, MalwareBytes, and most antivirus ware. Check your server files
for corruption after a clean restart of your system. Examine the hardware for damage too if the problems persist - eg. a
faulty power supply.

数据损坏
--------------

**症状**：World files fail to load or cause server to crash when players enter certain chunks. Database corruption.

**解决方案**：Load backup files of corrupted data. Software for repairing damaged worlds is available, and missing
regions may be regenerated. Investigate the cause of corruption - was it a malformed plugin, database driver, power
failure or something else? Always make sure you make regular backups of important data onto a secure device.

椅子到键盘之间的问题
----------------------------------

**症状**：昨天一切都工作得好好的。今天在我做了 ... 之后就变得奇怪了。

**解决方案**：SpongeDocs is not large enough to encompass the things people may do that will cause software to fail
in unpredictable ways. It is always worth thinking long and hard about what you may have done recently that could
have affected the smooth running of your server. A memory card may be loose after dusting, a shortcut may be broken...

Sponge 有 BUG
------------------------

**症状**：None of the above apply, and it still doesn't work as it should.

**解决方案**：Time to get out the big guns. File a report on the
`SpongeForge <https://github.com/spongepowered/SpongeForge/issues>`_ or
`SpongeVanilla <https://github.com/spongepowered/SpongeVanilla/issues>`_ issue tracker, remembering to include details
of the version of Forge and Sponge you are using, and a link to the relevant server log file.

宇宙中出现了某些错误
------------------------------------------

这个我们帮不了你。你只能靠你自己咯。
