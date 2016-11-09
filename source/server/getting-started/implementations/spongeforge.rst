======================
安装 SpongeForge
======================

SpongeForge 集成了 `Minecraft Forge <http://www.minecraftforge.net/>`__，所以它可以运行 Minecraft Forge
模组。事实上，Sponge 本身更像是一个 Forge 模组，继而在其上面加载 Sponge 插件，不过这是技术细节了。

不想使用 Minecraft Forge 的用户可以考虑 :doc:`spongevanilla`。

下载
========

详情请查看 :doc:`../../../downloads` 页面。

读懂下载文件名
=============================

当你下载 SpongeForge 时，文件的名称会提供一些重要的版本信息。它包含一个与该版本的 SpongeForge 兼容的 Forge
构建版本号。其它构建，甚至是只有一小个构建版本号的不同也会是不支持的。

但是，SpongeForge 通常会在新的 Forge 构建发布后快速地进行更新，所以你不必担心要为了运行 SpongeForge
而必须运行过时的 Forge 版本。


文件名的格式是 ``spongeforge-{MCVersion}-{ForgeVersion}-{SpongeAPIVersion}-{SpongeBuildId}``

+----------------------+----------------------------------------------------------------------------------------------+
| ``MCVersion``        | Minecraft 版本号。只有兼容该版本的客户端才能连接。                                           |
+----------------------+----------------------------------------------------------------------------------------------+
| ``ForgeVersion``     | 构建该文件使用的 Forge 版本。最好你的服务器应该运行对应版本的 Forge。                        |
+----------------------+----------------------------------------------------------------------------------------------+
| ``SpongeAPIVersion`` | 该文件实现的 SpongeAPI 版本。这是 Sponge 插件的依赖。                                        |
+----------------------+----------------------------------------------------------------------------------------------+
| ``SpongeBuildId``    | Sponge 的构建版本号。当你要反馈漏洞或寻求支持时应该提供的。                                  |
+----------------------+----------------------------------------------------------------------------------------------+

例子
~~~~~~~

文件名为 ``spongeforge-1.8-1577-3.0.0-BETA-1000.jar`` 兼容 Minecraft ``1.8`` 版本，需要 ``1.8-11.14.4.1577``
版本的 Forge，提供了 ``3.0.0`` 版本的 SpongeAPI 以及这是 SpongeForge 的第 ``1000`` 次构建。

.. note::

    一般的 Forge 模组通常能在指定的 Minecraft 版本（例如 1.8.0）下的任意一个 Forge
    构建中无错运行。然而，SpongeForge 除了其它方面外还需要访问 Forge
    的内部，这对于大多数模组而言是不应该触及的，更别说像 Sponge 那样进行修改。而 Forge
    只要想修改内部代码就可以自由地进行，所以其正常的向后兼容保证并不适用于 SpongeForge。


安装 SpongeForge
======================

.. note::

    如果你正在使用（或打算使用）游戏服务器托管，那或许会有能让你安装 Sponge 的控制面板。


.. warning::
  当你使用 Mojang 的安装程序时，Mojang 会使用他们自己的 Java
  版本而不会使用你的系统中安装的版本。安装程序目前为 Windows 附带了
  Java ``1.8.0_25`` 版本和为 OSX 附带了 Java ``1.8.0_60`` 版本。注意
  Sponge **最低** 需要 ``1.8.0_40`` 或更高版本才能正确地运行。你可以从这里获取不包含
  Java 的启动器：`官方 Minecraft 启动器 <https://minecraft.net/download>`_。

单人游戏 / 游戏内局域网服务器
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. 从 `Minecraft Forge 网站 <http://files.minecraftforge.net/>`_ 下载 Minecraft Forge
   安装程序。确保使用的是与 :doc:`下载的 Sponge 的文件名中列出的 <spongeforge>` **完全相同的构建版本号**。
#. 运行 Forge 安装程序。Minecraft 启动器中会创建一个新的 Forge 配置（profile）。
#. 打开 Minecraft 启动器，选择这个新的 Forge 配置。
#. 点击 "Options" 并点击 "Open Game Dir"。
#. 从 Sponge 网站下载 SpongeForge 并放入 ``mods`` 文件夹中。如果文件夹不存在则创建它。
#. Sponge 应该已经能在单人游戏以及局域网工作了。

下一步，学习如何 :doc:`配置 Sponge <../configuration/index>` 与
:doc:`管理 Sponge 实例 </server/management/index>` （包括安装插件）。

专用服务器
~~~~~~~~~~~~~~~~~

.. note::

    如果你已经拥有 Forge 服务器了，则只需将 Sponge 模组放入 ``mods``
    文件夹中。记住要将你的 Forge 更新到与 :doc:`sponge 要求 <spongeforge>` 相匹配的版本。

通过命令行安装 Forge
--------------------------------

1. 访问 `Minecraft Forge 网站 <http://files.minecraftforge.net/>`_ 并点击 "Show all downloads"
   查看可用项的完整列表。确定一个与 :doc:`下载的 Sponge 的文件名中 <spongeforge>`
   列出的相匹配的版本，然后将鼠标悬停在 "Installer" 旁边的 (i) 上获取下载直链。
#. 用你最喜欢的下载方式将 jar 下载到相应位置。例如：``wget http://url.to/forge-version-installer.jar``
#. 在你希望安装 Forge 的文件夹中，用 ``--installServer`` 选项执行
   jar。例如：``java -jar forge-version-installer.jar --installServer``
#. 按下文继续将 SpongeForge 添加到 Forge 中。


通过图形用户界面安装 Forge
--------------------------

1. 从 `Minecraft Forge 网站 <http://files.minecraftforge.net/>`_ 下载与
   :doc:`下载的 Sponge 的文件名中 <spongeforge>` 列出的相匹配的版本的 Minecraft Forge 安装程序。
#. 运行 Forge 安装程序，选择 "Install Server"，选择一个空文件夹来放服务端文件，点击 OK。
#. 按下文继续将 SpongeForge 添加到 Forge 中。


添加 SpongeForge 到 Forge
---------------------------

1. 从 Sponge 网站下载 SpongeForge 并放入你的服务端目录的 ``mods`` 文件夹中。如果文件夹不存在则创建它。
#. 现在你可以通过命令行或者启动脚本 ``java -jar forge-version-XYZ.jar`` 启动服务端了。
#. 如果是在家庭中操作的，配置 :doc:`../port-forward` 来确保其他人能够连接。

下一步，学习如何 :doc:`配置 Sponge <../configuration/index>` 与
:doc:`管理 Sponge 实例 </server/management/index>` （包括安装插件）。

链接
=====

* `主页 <http://spongepowered.org/>`__
* `GitHub <https://github.com/SpongePowered/SpongeForge>`__
