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

The layout of our branches (described below) is designed to assist this process by allowing us to make minor releases
without a breaking change forcing us to make it a major release. This branch layout applies to the SpongeAPI,
SpongeCommon, SpongeForge, and SpongeVanilla repositories but not to the SpongeDocs.

SpongeAPI, SpongeCommon, SpongeForge and SpongeVanilla
======================================================

The Core Branches
~~~~~~~~~~~~~~~~~

There are three branches which form the core of our repositories; they are ``master``, ``bleeding``, and
``release``. The ``master`` and ``bleeding`` branches are for active development and the ``release`` branch tracks
the commit as of the most recent release build.

The key differences between the ``master`` and ``bleeding`` branches is that any ``feature`` branches which are
breaking *must* be merged into the bleeding branch. This allows the ``master`` branch to only contain
backwards-compatible changes allowing minor versions to be released based on it if necessary.

Release Branches
~~~~~~~~~~~~~~~~

Prior to releasing builds the content of the release should be first moved to a release prep branch.
This branch allows dedicated testing to be performed for a release without forcing a code freeze on
the development branches. Any bugfixes applied to the ``release`` branch are merged back to the ``master``
branch when the release is finalized. Once a release is made the version of the ``master`` and ``bleeding``
branches are both updated: the ``master`` branch to the next minor version and the ``bleeding`` branch to
the next major version (assuming it was not already on the next major version).

Hotfix Branches
~~~~~~~~~~~~~~~

If after a release is made, and a significant bug is found, a ``hotfix/foo`` branch can be created based on the
last release version and a new release can be made from this hotfix branch with the patch version
incremented by one. The hotfix branch can then be merged back into ``master`` for inclusion into future
versions.

Feature Branches
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

Core Branch
~~~~~~~~~~~

The core branch for the SpongeDocs is ``master``. Each new commit to ``master`` triggers a rebuild of the `docs website
<https://docs.spongepowered.org/>`_. Commits to ``master`` are generally only made when a feature branch is merged or
a small fix not requiring review is made by SpongeDocs Staff.

Feature Branches
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

Release Branches
~~~~~~~~~~~~~~~~

If two or more feature branches are waiting on the release of their corresponding API version, they will be accumulated
in a ``release/x.y.z`` branch before being merged into master so that any conflics may be resolved beforehand.

.. image:: /images/contributing/versioning-future-release-branch.svg
    :alt: future release branch example
