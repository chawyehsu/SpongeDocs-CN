===============
安装 Java
===============

运行 Sponge 与 Minecraft 需要 Java。或许你已经安装了 Java，但你可能需要升级 Java 版本。

目前 Sponge 需要 Java 8（明确地是 ``1.8.0_40`` 或以上版本）。旧版 Java 已经过时并且不能用于运行
Sponge。Java 各个主要版本（6，7，8）之间的区别显著，使用旧版本不能正确地运行 Sponge。

安装 Java
===============

如果你的计算机使用 Windows 或是 Mac OS X，你可以 `从官方网站下载 Java
<https://java.com/en/download/manual.jsp>`__。

Linux 用户则可以通过包管理器安装 OpenJDK。OpenJDK 是 Oracle Java
的开源版本，虽然不比后者好，也能正常使用。当然你也可以 `下载 Linux 版本的 Oracle Java
<http://www.oracle.com/technetwork/java/javase/downloads/index.html>`__，但要知道，很多依赖
Java 的 Linux 应用程序仍然会安装 OpenJDK。

32 位与 64 位
~~~~~~~~~~~~~~~~~

如果你的计算机支持 64 位，那就尽可能地安装使用 64 位的 Java。上述网站链接中的
Java 安装程序会检测你的计算机是否支持 64 位。

因为 64 位的 Java 运行起来更好，并且能使用超过 3GB 的内存，所以我们一般不推荐使用 32 位。

大多数现代的计算机都支持 64 位。

JDK 与 JRE
~~~~~~~~~~~

JRE（Java 运行时环境）是用来运行 Java 应用程序的。上文中的下载链接页面提供的就是 JRE。

JDK（Java 开发工具包）是用来创建 Java 应用程序的。你一般不需要它，除非你打算编写 Sponge
插件或是参与 Sponge 开发。不过，某些情况下你可能需要用 JDK 去诊断 Java
应用程序（例如 Sponge）的运行情况。这时你可以从另外一个网页上 `下载 JDK
<http://www.oracle.com/technetwork/java/javase/downloads/index.html>`__。
