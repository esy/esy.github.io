---
id: what-why
title: What & Why
---

* Project metadata is managed inside `package.json`.

* Parallel builds.

* Clean environment builds for reproducibility.

* Global build cache automatically shared across all projects — initializing new
  projects is often cheap.

* File system sandboxing to prevent builds from mutating locations they don't
  own.

* Solves environment variable pain. Native toolchains rely heavily on environment
  variables, and `esy` makes them behave predictably, and usually even gets them
  out of your way entirely.

* Allows symlink workflows for local development (by enforcing out-of-source
  builds). This allows you to work on several projects locally, make changes to
  one project and the projects that depend on it will automatically know they
  need to rebuild themselves.

* Run commands in project environment quickly `esy <anycommand>`.

* Makes sharing of native projects easier than ever by supporting "eject to `Makefile`".

  * Build dependency graph without network access.

  * Build dependency graph where `node` is not installed and where no package
    manager is installed.
