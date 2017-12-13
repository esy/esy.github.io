---
id: for-opam-users
title: For OPAM users
---

For those who familiar with [OPAM][], esy provides a powerful alternative (to
the `opam` tool, OPAM packages are still accessible with Esy):

* Manages OCaml compilers and dependencies on a per project basis.

* Sandboxes project environment by exposing only those packages which are
  defined as dependencies.

* Fast parallel builds which are agressively cached (even across different projects).

* Keeps the ability to use packages published on OPAM repository.
