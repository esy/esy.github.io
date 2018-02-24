---
id: development
title: Development
---

* [Testing Locally](#testing-locally)
* [Running Tests](#running-tests)
* [Issues](#issues)
* [Publishing Releases](#publishing-releases)

To make changes to `esy` and test them locally:

```bash
git clone git://github.com/esy/esy.git
cd esy
make bootstrap
```

Run:

```bash
make
```

to see the description of development workflow.

### Testing Locally

```bash
make build-release
npm remove -g esy
npm install -g dist
```

Now you may run `esy` commands using your local version of `esy`.

> You don't have to install local version of esy globally if you're in the middle of developing something.
> Just running `PATH_TO_ESY/bin/esy` will work, too.

### Running Tests

```bash
make test
```

### Issues

Issues are tracked at [esy/esy](https://github.com/esy/esy).

### Publishing Releases

On a clean branch off of `origin/master`, run:

```bash
make bump-patch-version publish
```

to bump the patch version, tag the release in git repository and publish the
tarball on npm.

To publish under a custom release tag:

```bash
make RELEASE_TAG=next bump-patch-version publish
```

Release tag `next` is used to publish preview releases.
