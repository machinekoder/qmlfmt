[![Build Status](https://travis-ci.org/jesperhh/qmlfmt.svg?branch=master)](https://travis-ci.org/jesperhh/qmlfmt)
[![Build status](https://ci.appveyor.com/api/projects/status/qti9p9s9q9r3pkoo/branch/master?svg=true)](https://ci.appveyor.com/project/jesperhh/qmlfmt/branch/master)

# qmlfmt
qmlfmt - command line application that formats QML files

## Build instructions
Requires
- CMake 3.0 or later
- Qt 5.2 or later.
- Tested with Visual Studio 2017 and mingw 4.9.1.
- Tested with Ubuntu Bionic (18.04) and gcc 7.3.0
- Optionally QtCreator source code.
  - If not present, it will be downloaded as part of the build.

### Linux

Install build dependencies:
```bash
sudo apt install cmake qtbase5-dev qtdeclarative5-dev
```

Build and install qmlfmt
```bash
cd <source dir>
cmake .
make
sudo make install
```


## Usage
    Usage: qmlfmt [options] path

Without an explicit path, it processes the standard input. Given a file, it operates on that file; given a directory, it operates on all qml files in that directory, recursively. (Files starting with a period are ignored.) By default, qmlfmt prints the reformatted sources to standard output.

### Options:
    -?, -h, --help  Displays this help.
    -v, --version   Displays version information.
    -d              Do not print reformatted sources to standard output. If a
                    file's formatting is different than qmlfmt's, print diffs to
                    standard output.
    -e              Print all errors.
    -l              Do not print reformatted sources to standard output. If a
                    file's formatting is different from qmlfmt's, print its name
                    to standard output.
    -w              Do not print reformatted sources to standard output. If a
                    file's formatting is different from qmlfmt's, overwrite it
                    with qmlfmt's version.
    -i <indentSize> Indentation size.
    -t <tabSize>    Tab size.

### Arguments:
    path            file or directory to process. If not set, qmlfmt will process
                    the standard input.

## Version control integration

Use [pre-commit](https://pre-commit.com/). Once you [have it
installed](https://pre-commit.com/#install), add this to the
`.pre-commit-config.yaml` in your repository
(be sure to update `rev` to point to a real git tag/revision!)::

```yaml
repos:
-   repo: https://github.com/machinekoder/qmlfmt
    rev: '' # Update me!
    hooks:
    - id: qmlfmt
      args: [-i 2, -t 2]
```

Then run `pre-commit install` and you're ready to go.
