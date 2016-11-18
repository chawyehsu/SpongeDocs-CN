========================
创建启动脚本
========================

.. note::

    这些说明只在你打算在你自己的机器上运行你的 Minecraft 服务器时适用。大多数共享 Minecraft 主机会为你创建启动脚本。

编写启动脚本
=======================

首先，打开一个文本编辑器，比如 Atom，Sublime Text
或者记事本。编写（或粘贴）用于你服务器的启动脚本。Windows，Mac OS X 以及 Linux
的启动脚本示例已在下面提供。但请谨记你的机器的内存限制。

.. note::

    下面的例子是通用的。对于使用了 Sponge (coremod) 的 Forge 服务端，将 ``forge-1.8-XYZ-universal.jar``
    修改为在你服务器目录下的任意版本 Forge 的名字。要启动 SpongeVanilla 服务端，则将
    ``forge-1.8-XYZ-universal.jar`` 修改为 SpongeVanilla.jar 文件的名字。

Windows
~~~~~~~

.. code-block:: none

    java -Xms1G -Xmx2G -jar forge-1.8-XYZ-universal.jar
    pause

将你的 Windows 启动脚本保存为 ``launch.bat``。

Mac OS X
~~~~~~~~

.. code-block:: none

    #!/bin/bash
    cd "$(dirname "$0")"
    java -Xms1G -Xmx2G -jar forge-1.8-XYZ-universal.jar

将你的 Mac 启动脚本保存为 ``launch.command``。

Linux
~~~~~

.. code-block:: none

    #!/bin/sh
    cd "$(dirname "$(readlink -fn "$0")")"
    java -Xms1G -Xmx2G -jar forge-1.8-XYZ-universal.jar

将你的 Linux 启动脚本保存为 ``launch.sh``。

运行启动脚本
=======================

确保你是在特别为你的服务器创建的文件夹中运行启动脚本。这是为了你好；不幸的是，如果你不这么做，Spongie
也没有办法吸干你的眼泪。

你可以通过双击它来运行你的启动脚本。如果你正在使用控制台或者终端，切换到该脚本的目录下并运行它。请记
住，为了运行服务器你必须同意 Mojang EULA。

.. note::

    Sponge 禁用了 Minecraft 服务端默认的 GUI 控制台，因为它太消耗处理器资源了。

.. warning::

    如果你尝试在 Mac 上启动你的服务器时出现权限错误，试试这个：

    * 打开终端。
    * 输入 ``chmod a+x``，结尾加一个空格。
    * 将你的启动脚本拖到终端中。
    * 按回车键。
