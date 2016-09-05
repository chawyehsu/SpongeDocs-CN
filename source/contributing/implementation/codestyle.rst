==========
代码规范
==========

我们大致遵循 `Google 的 Java 风格指南 <https://google.github.io/styleguide/javaguide.html>`_
并有一些微小补充与修改，下文将具体介绍。

.. tip::
    你可以使用我们的代码规范预设来让 IDE 为你自动格式化代码。详见 :doc:`../../preparing/index`。

* 行结束符

  * 在提交时使用 Unix 行结束符（\\n）

    * Windows 的 Git 用户可以执行 ``git config --global core.autocrlf true`` 来让 Git 进行自动转换

* 列宽

  * Javadoc 80 字符
  * 代码 150 字符
  * 如果对提高可读性有帮助，请自由换行

* 缩进

  * 使用 4 个而不是 2 个空格来缩进

* 空行

  * 在每个类、接口、枚举等的第一个成员前（例如在 ``class Example {`` 之后）和最后一个成员后放一个空行

* 文件头

  * 文件头必须包含项目的许可头。使用 Gradle 的 ``licenseFormat`` 任务来自动添加。

* 引入

  * 引入必须以下列方式分组，每组之间以一个空行分隔

    * 静态引入
    * 所有其它引入
    * ``java`` 引入
    * ``javax`` 引入

  * 这与 Google 把引入以顶层包分组的风格不同，我们将它们全部分在同一组。

* 异常

  * 对于被忽略的异常，请将异常变量命名为 ``ignored``

* 字段访问

  * 使用 ``this`` 来访问 **所有的** 成员

* Javadocs

  * 不要使用 ``@author``
  * 用 ``<p>`` 和 ``</p>`` 包裹段落
  * 每个 ``@语句`` 的描述部分首字母大写。例如 ``@param name Player to affect``，不要有句号

代码约定
================

* 在 API 中使用 :doc:`/plugin/optional/index` 而不是返回 ``null``
* 所有可接受 ``null`` 的方法参数必须注解为 ``@Nullable`` （位于 javax.*），所有的方法和参数默认均为 ``@Nonnull``。
* 使用 `Google Preconditions <https://code.google.com/p/guava-libraries/wiki/PreconditionsExplained>`_
  进行 null 与参数的检测。

Gist
========

尽管我们强烈建议你阅读 Google 的 Java
代码约定，但是它们实在是太长了。为了帮助你快速开始，下面是一个格式正确的代码样例：

.. code-block:: java

    /*
     * This file is part of Sponge, licensed under the MIT License (MIT).
     *
     * Copyright (c) SpongePowered.org <http://www.spongepowered.org>
     * Copyright (c) contributors
     *
     * Permission is hereby granted, free of charge, to any person obtaining a copy
     * of this software and associated documentation files (the "Software"), to deal
     * in the Software without restriction, including without limitation the rights
     * to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
     * copies of the Software, and to permit persons to whom the Software is
     * furnished to do so, subject to the following conditions:
     *
     * The above copyright notice and this permission notice shall be included in
     * all copies or substantial portions of the Software.
     *
     * THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
     * IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
     * FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
     * AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
     * LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
     * OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
     * THE SOFTWARE.
     */
    package com.example.java;

    import org.slf4j.Logger;
    import org.slf4j.LoggerFactory;

    import java.util.Random;
    import java.util.Optional;

    public class Example {

        private static final Logger log = LoggerFactory.getLogger(Example.class);
        private static final Random random = new Random();
        private final String id = "test";

        /**
         * Returns an identifier approximately half of the time.
         *
         * <p>A static instance of {@link Random} is used to calculate the
         * outcome with a 50% chance.</p>
         *
         * @return The ID, if available
         */
        public Optional<String> resolveId() {
            log.info("ID requested");

            if (random.nextBoolean()) {
                return Optional.of(this.id);
            } else {
                return Optional.empty();
            }
        }

        /**
         * Returns an identifier approximately half of the time.
         *
         * <p>A static instance of {@link Random} is used to calculate the
         * outcome with a 50% chance. If the outcome is to not return the ID,
         * the given fallback ID is returned.</p>
         *
         * @param fallback A fallback name to return
         * @return The ID half of the time, the given fallback the other half
         */
        public String resolveId(String fallback) {
            return resolveId().orElse(fallback);
        }

    }
