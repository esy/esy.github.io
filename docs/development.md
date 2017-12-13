---
id: development
title: Development
---

* [Testing Locally](#testing-locally)
* [Running Tests](#running-tests)
* [Issues](#issues)
* [Publishing Releases](#publishing-releases)

To make changes to `esy` and test them locally:

```
% git clone git://github.com/esy/esy.git
% cd esy
% make bootstrap
```

Run:

```
% make
```

to see the description of development workflow.

### Testing Locally

```
% make build-release
% npm remove -g esy
% npm install -g dist
```

Now you may run `esy` commands using your local version of `esy`.

### Running Tests

```
% make test
```

### Issues

Issues are tracked at [esy/esy][].

### Publishing Releases

On a clean branch off of `origin/master`, run:

```
% make bump-patch-version publish
```

to bump the patch version, tag the release in git repository and publish the
tarball on npm.

To publish under custom release tag:

```
% make RELEASE_TAG=next bump-patch-version publish
```

Release tag `next` is used to publish preview releases.

[esy-ocaml-project]: https://github.com/esy-ocaml/esy-ocaml-project
[esy-reason-project]: https://github.com/esy-ocaml/esy-reason-project
[esy/esy]: https://github.com/esy/esy
[esy-ocaml/esy-install]: https://github.com/esy-ocaml/esy-install
[esy-ocaml/esy-opam]: https://github.com/esy-ocaml/esy-opam
[opam]: https://opam.ocaml.org
[npm]: https://npmjs.org
[reason]: https://reasonml.github.io
[ocaml]: https://ocaml.org
[jbuilder]: http://jbuilder.readthedocs.io
[ocamlbuild]: https://github.com/ocaml/ocamlbuild/blob/master/manual/manual.adoc
[pjc]: https://github.com/jordwalke/PackageJsonForCompilers
