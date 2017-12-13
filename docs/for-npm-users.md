---
id: for-npm-users
title: For NPM users
---

For those familiar with [npm][], esy allows to work with Reason/OCaml projects
within the familiar npm-like workflow:

* Declare dependencies in `package.json`.

* Install and build with `esy install` and `esy build` commands. Dependencies'
  source code end up in `node_modules`.

* Share your work with other developers by publishing on npm registry and/or github.

* Access packages published on [OPAM][] (a package registry for OCaml) via
  `@opam` npm scope (for example `@opam/lwt` to pull `lwt` library from OPAM).
