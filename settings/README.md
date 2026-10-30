# Shared repository defaults

This policy keeps repository administration consistent while leaving project identities and verification contracts with their owners.

<!-- toc:start -->
**Table of contents**

- [Policy boundaries](#policy-boundaries)
- [Configuration hierarchy](#configuration-hierarchy)
- [Change and verification](#change-and-verification)
<!-- toc:end -->

## Policy boundaries

[defaults.yml](defaults.yml) defines private visibility, the main default branch, auto-merge capability, squash merging, a common label catalog and branch protections. Auto-merge still requires each pull request to satisfy its reviews and checks.

The synchronization audience consists of private and internal repositories in the selected organization. Public repositories are excluded. The configuration does not change another organization's settings.

Required check names and stronger project protections are preserved as private overrides. Internal visibility is an explicit project override. Extra project labels are retained through safe-settings' additive label mode.

## Configuration hierarchy

The public defaults contain reusable policy only. The organization's private admin repository holds project metadata, one source-ready branch group and per-project verification exceptions in safe-settings' native `settings.yml`, `suborgs/` and `repos/` hierarchy.

Safe-settings reads one admin repository. The private admin policy therefore contains a generated copy of these defaults with content provenance. Changes are promoted through a reviewed source update before synchronization. The public source remains the maintained default definition.

Project repositories do not need copies of the complete policy. Publish and validate the central configuration first. Retire each former project settings file before the first central write, so policy ownership has one active path.

## Change and verification

Review changes to the generic defaults here. Validate them against the pinned upstream safe-settings component models, regenerate the private admin policy, and review the affected effective configurations before applying them. Validate visibility and organization ownership again immediately before a settings mutation.

Empty repositories can inherit metadata defaults without creating source files. Their branch protection becomes applicable when the main branch exists. Existing histories must be preserved when normalizing a default branch.
