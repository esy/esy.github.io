---
id: commands
title: Commands
---

```
Usage: esy <command> [--help] [--version]

install               Installs packages declared in package.json.
i

build                 Run build commands for the project.
b                     (as specified in "esy.build" key within package.json)

add <package>         Add a specified package to dependencies and installs it.

ls-builds             Lists package dependencies along with each package's build status.
                      This will include transitive package dependencies.

ls-libs [--all]       Lists package dependencies along with the set of libraries made
                      available by each package dependency. By default, only includes
                      immediate package dependencies.  Pass `--all` to include
                      transitive dependencies.

print-env             Prints esy environment on stdout.

build-shell [path]    Drops into a shell with environment matching your
                      package's build environment. If argument is provided
                      then it should point to the package inside the current
                      sandbox — that will initialize build shell for that
                      specified package.

shell                 Drops into development shell.
                      Less strict than build-shell and allows access to
                      devDependencies.

version               Print esy version and exit

build <command>       Run command inside the build environment.
b <command>

x <command>           Run command as if the package is already installed.
                      Useful for testing.

<command>             Executes <command> as if you had executed it inside of
                      esy shell.

help                  Show detailed help.
```
