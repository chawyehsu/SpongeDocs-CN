# Sponge Documentation CN :cn:

这里是 Sponge 官方文档的其中一个民间**非官方**中文翻译版本的仓库。  
建立此仓库的目的是在 Sponge 官方文档仍在不断迭代的状态下，
形成一份相对独立稳定的中文文档，目前主力翻译与维护着 v3.1.0 版本的文档。
*（说白了，官方文档的频繁更新不利于翻译的进行）* :new_moon_with_face:

建议查看 Sponge 官方完整的多语言在线文档，以获取**最新**的文档资料。地址：[Sponge Docs](https://docs.spongepowered.org/)

## 参与官方在线翻译

建议前往 Sponge 官方的翻译地址参与官方翻译工作：[CrowdIn 翻译页](https://translate.spongepowered.org)。

## 参与本仓库的翻译

配置本地翻译与构建环境：

1. [安装 Python 2.7 与 Sphinx](http://sphinx-doc.org/latest/install.html)
2. [安装 node.js](http://nodejs.org/download/)

在项目目录下执行：

	npm install -g gulp
	npm install
	pip install -r etc/requirements.txt
	gulp

将会在本地监听 ``http://localhost:8000``，并自动启动浏览器打开页面，对文档做修改后页面会自动刷新。
