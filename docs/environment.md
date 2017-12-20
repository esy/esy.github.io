---
id: environment
title: Environment
---

* [Exported Environment](#exported-environment)
* [Esy Environment Reference](#esy-environment-reference)
* [Build Environment](#build-environment)
* [Command Environment](#command-environment)
* [Variable substitution syntax](#variable-substitution-syntax)

#### Exported Environment

Packages can configure how they contribute to the environment of the packages
which depend on them.

To add a new environment variable to the Esy [build
environment](#build-environment) packages could specify `esy.exportedEnv` config
key:

```
{
  "name": "mylib",
  "esy": {
    ...,
    "exportedEnv": {
      "CAML_LD_LIBRARY_PATH": "#{mylib.lib : $CAML_LD_LIBRARY_PATH}",
      "scope": "global"
    }
  }
}
```

In the example above, the configuration _exports_ (in this specific case it
_re-exports_ it) an environment variable called `$CAML_LD_LIBRARY_PATH` by
appending `$mylib__lib` to its previous value.

Also note the usage of [Esy variable substitution
syntax](#variable-substitution-syntax) to define the value of the
`$CAML_LD_LIBRARY_PATH` variable.

### Esy Environment Reference

For each project Esy manages:

* _build environment_ — an environment which is used to build the project

* _command environment_ — an environment which is used running text editors/IDE
  and for general testing of the built artfiacts

#### Build Environment

The following environment variables are provided by Esy:

* `$SHELL`
* `$PATH`
* `$MAN_PATH`
* `$OCAMLPATH`
* `$OCAMLFIND_DESTDIR`
* `$OCAMLFIND_LDCONF`
* `$OCAMLFIND_COMMANDS`

#### Command Environment

Currently the command environment is identical to build environment sans the
`$SHELL` variable which is non-overriden and equals to the `$SHELL` value of a
user's environment.

### Variable substitution syntax

Your `package.json`'s `esy` configuration can include "interpolation" regions written
as `#{ }`, where `esy` "variables" which will automatically be substituted
with their corresponding values.

For example, if you have a package named `@company/widget-factory` at version
`1.2.0`, then its `esy.build` field in `package.json` could be specified as:

```json
   "build": "make #{@company/widget-factory.version}",
```

and `esy` will ensure that the build command is interpreted as `"make 1.2.0"`.
In this example the interpolation region includes just one `esy` variable
`@company/widget-factory.version` - which is substituted with the version number
for the `@company/widget-factory` package.

Package specific variables are prefixed with their package name, followed
by an `esy` "property" of that package such as `.version` or `.lib`.

`esy` also provides some other built in variables which help with path and environment
manipulation in a cross platform manner.

**Supported Variable Substitutions:**

Those variables refer to the values defined for the current package:

* `self.bin`
* `self.sbin`
* `self.lib`
* `self.man`
* `self.doc`
* `self.stublibs`
* `self.toplevel`
* `self.share`
* `self.etc`
* `self.install`
* `self.target_dir`
* `self.root`
* `self.name`
* `self.version`
* `self.depends`

You can refer to the values defined for other packages by using the respective
`package-name` prefix:

* `package-name.bin`
* `package-name.sbin`
* `package-name.lib`
* `package-name.man`
* `package-name.doc`
* `package-name.stublibs`
* `package-name.toplevel`
* `package-name.share`
* `package-name.etc`
* `package-name.install`
* `package-name.target_dir`
* `package-name.root`
* `package-name.name`
* `package-name.version`
* `package-name.depends`

The following constructs are also allowed inside "interpolation" regions:

* `$PATH`, `$cur__bin` : environment variable references
* `'hello'`, `'lib'` : string literals
* `/` : path separator (substituted with the platform's path separator)
* `:` : env var value separator (substituted with platform's env var separator `:`/`;`).

You can join many of these `esy` variables together inside of an interpolation region
by separating the variables with spaces. The entire interpolation region will be substituted
with the concatenation of the space separated `esy` variables.

White space separating the variables are not included in the concatenation, If
you need to insert a literal white space, use `' '` string literal.

Examples:

* ```
  "#{pkg.bin : $PATH}"
  ```

* ```
  "#{pkg.lib / 'stublibs' : $CAML_LD_LIBRARY_PATH}"
  ```
