# Shared repository settings

<!-- toc:start -->
**Table of contents**

- [Shared repository settings](#shared-repository-settings)
<!-- toc:end -->

[`settings.yml`](settings.yml) defines generic defaults for repository merge behavior,
labels and main-branch protection. Each adopting project owns its minimal override
in `.github/settings.yml`. The effective configuration merges these two locations;
project-specific files are not collected in a central `settings/repos` directory.

Mappings merge recursively and named branch/label collections merge by `name`.
Other lists, scalars and explicit nulls replace inherited values. Missing fields
inherit. Project identity, CI check/app bindings, visibility exceptions and explicit
governance choices belong downstream.

The scheduled consumer validates immutable source revisions and builds temporary
native configuration. Repository visibility and authorization determine its scope.
Publishing these generic defaults does not change this repository's own settings.
