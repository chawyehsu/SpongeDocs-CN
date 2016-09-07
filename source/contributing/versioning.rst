==============================================
版本控制系统与仓库分支结构
==============================================

随着 beta 版的发布，我们已经将 SpongeAPI 的版本号迁移至语义化版本（见
http://semver.org/）。这个更改意味着每一次我们发布一个新版本时我们必须根据
semver 的规则对版本号进行递增。

SemVer
======

SemVer 使用 ``X.Y.Z`` 体系，``X`` 是 *主* 版本号，``Y`` 是 *次* 版本号以及 ``Z`` 是 *修订* 号。
一个包含不能向下兼容的更改的发布必须比以前的发布大一个 *主*
版本号。如果仅有仍然向下兼容的新特性，则新发布将比以前的发布大一个 *次*
版本号，而如果发布仅仅只包含错误修正，则只递增一个 *修订* 号。

这就是说例如 ``3.2.0`` 是与 ``3.0.0`` 完全兼容的，``4.0.0`` 则与 ``3.0.0``
非二进制兼容。而 ``3.1.0`` 与 ``3.1.2`` 除了 BUG 修复之外是完全可互换的。

下文所述的分支结构被设计允许我们在没有重大更改时进行次版本而不是主版本的发布。这个分支结构适用于
SpongeAPI、SpongeCommon、SpongeForge 以及 SpongeVanilla 的仓库，不适用于 SpongeDocs。

SpongeAPI，SpongeCommon，SpongeForge 和 SpongeVanilla
======================================================

核心分支
~~~~~~~~~~~~~~~~~

我们的仓库的核心分支有三个，它们分别是 ``master``，``bleeding`` 和 ``release``。``master`` 和 ``bleeding``
分支用于进行开发，``release`` 分支则追踪最新发布构建的提交。

``master`` 和 ``bleeding`` 的关键不同点是，任何重大的 ``feature`` 分支 *必须* 合并进 ``bleeding``
分支。而 ``master`` 分支只包含向下兼容的修改，必要时仅允许发布次版本。

发布分支
~~~~~~~~~~~~~~~~

在发布构建之前，发布的内容应该先移动到一个预备分支。在这个分支上允许为一个发布进行专门的测试，
而不会强制冻结开发分支。当发布最终定稿时，所有应用到 ``release`` 分支上的漏洞修复都将合并回 ``master``
分支。一旦发布完成，``master`` 和 ``bleeding`` 分支都将会更新：``master`` 分支到下一个次版本，``bleeding``
分支到下一个主版本（假设此前还没准备到下一个主版本）。

热修复分支
~~~~~~~~~~~~~~~

如果在一个发布完成后发现了一个重大的漏斗，则可以基于最后一个发布版本创建一个 ``hotfix/foo``
分支，并基于这个热修复分支以递增一个修订版本作出一个新的发布。然后热修复可以合并回 ``master``
分支包含进后续的版本中。

特性分支
~~~~~~~~~~~~~~~~

New features or changes will continue to be done in a ``feature/foo`` or ``fix/bar`` branch. When merging
back into a development branch (``master`` or ``bleeding``) you should consider whether the changes are
breaking or are strictly backwards-compatible. If the changes are purely new features, or
binary-compatible bugfixes, then the feature branch can be merged into the ``master`` branch. If the
changes include any breaking changes however, then the feature branch must be merged into the
``bleeding`` branch to be included in the next major release.

SpongeDocs
==========

The SpongeDocs themselves are unversioned following our philosophy that they will never be finished, but instead in a
constant flux of ever increasing usability. However they *target* a specific version of the API, generally the most
recent *release* of SpongeAPI.

核心分支
~~~~~~~~~~~

The core branch for the SpongeDocs is ``master``. Each new commit to ``master`` triggers a rebuild of the `docs website
<https://docs.spongepowered.org/>`_. Commits to ``master`` are generally only made when a feature branch is merged or
a small fix not requiring review is made by SpongeDocs Staff.

特性分支
~~~~~~~~~~~~~~~~

Whenever a new feature is described, older texts are updated or reworded or the documents are restructured it is done
in a ``feature/foo`` or ``fix/bar`` branch. Those branches will then be reviewed and, once they are deemed complete,
may be merged.

A feature branch may only be merged into master if the changes / additions made in it are correct regarding the
**SpongeAPI release currently targeted by the SpongeDocs**. Any feature branches that describe features not yet included
in a release stay unmerged until the corresponding API version is released and becomes the new targeted version for the
SpongeDocs.

.. image:: /images/contributing/versioning-release-branch.svg
    :alt: release branch example

发布分支
~~~~~~~~~~~~~~~~

If two or more feature branches are waiting on the release of their corresponding API version, they will be accumulated
in a ``release/x.y.z`` branch before being merged into master so that any conflics may be resolved beforehand.

.. image:: /images/contributing/versioning-future-release-branch.svg
    :alt: future release branch example
