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

    If you use (or are planning to use) a game server host, they may have a control panel that can install Sponge for you.


.. warning::
  When using the Mojang installer, Mojang makes use of their own Java version and not the one you installed on your
  system. The installer currently ships with Java ``1.8.0_25`` for Windows and ``1.8.0_60`` for OSX. Note that Sponge
  requires **at least** ``1.8.0_40`` or above to run properly. You can grab the Launcher without included Java here:
  `official Minecraft Launcher <https://minecraft.net/download>`_

单人游戏 / 游戏内局域网服务器
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Download the Minecraft Forge installer from the `Minecraft Forge website <http://files.minecraftforge.net/>`_. Make
   sure to use **exactly the same build number** as :doc:`the one listed in the filename of the Sponge download
   <spongeforge>`.
#. Run the provided Forge installer. A new Forge profile will be created in the Minecraft launcher.
#. Open the Minecraft launcher, and select the new Forge profile.
#. Click "Options" and click "Open Game Dir".
#. Download SpongeForge from the Sponge website and put it into the ``mods`` folder. Create the folder if it does
   not yet exist.
#. Sponge should work in both in single player and if you open your world to LAN.

Next, learn how you can :doc:`configure Sponge <../configuration/index>` and how to
:doc:`manage your instance of Sponge </server/management/index>` (including installing plugins).

独立服务器
~~~~~~~~~~~~~~~~~

.. note::

    If you already have a Forge server, just put the Sponge mod into your ``mods`` folder. Remember to update your Forge
    version to match the one that :doc:`sponge requires <spongeforge>`.

通过命令行安装 Forge
--------------------------------

1. Visit the `Minecraft Forge website <http://files.minecraftforge.net/>`_ and click "Show all downloads" to view the full
   set of available options. Identify the version matching the one listed :doc:`in the filename of the SpongeForge download
   <spongeforge>`, and hover over the (i) next to "Installer" to get the direct download link.
#. Use your favorite download method to download the jar to its destination.
   Example: ``wget http://url.to/forge-version-installer.jar``
#. From the folder in which you wish to install Forge, execute the jar with the ``--installServer`` option. Example:
   ``java -jar forge-version-installer.jar --installServer``
#.  Continue to Adding SpongeForge to Forge below.


通过图形用户界面安装 Forge
--------------------------

1. Download the Minecraft Forge installer from the `Minecraft Forge website <http://files.minecraftforge.net/>`_ for the version
   matching the one listed :doc:`in the filename of the SpongeForge download <spongeforge>`.
#. Run the provided Forge installer, select "Install Server", choose an empty folder to place the server's files,
   and then click OK.
#. Continue to Adding SpongeForge to Forge below.


添加 SpongeForge 到 Forge
---------------------------

1. Download SpongeForge from the Sponge website and put it into the ``mods`` folder in your server directory.
   Create the folder if it does not yet exist.
#. You may now launch the server via command or launch script ``java -jar forge-version-XYZ.jar``.
#. If operating from home, set up :doc:`../port-forward` to ensure others can connect.

Next, learn how you can create and use a :doc:`launch-script <../launch-script>`,
:doc:`configure Sponge <../configuration/index>` and :doc:`manage your server
</server/management/index>` (including installing plugins).

链接
=====

* `主页 <http://spongepowered.org/>`__
* `GitHub <https://github.com/SpongePowered/SpongeForge>`__
