{{ cookiecutter.project_name }}
==========

TLDR for contributing
---------------------

- Clone the project
- Run `./autogen.sh`
- Head to `build/debug`
- Run `./configure`
- Build with `make`
- Test with `make check`

Contributing
------------

The original repository only contains raw `autoconf` / `automake` files. It
does _not_ contain generated artifacts such as the `configure` script.

If you are working direcly from the version controlled repository, you will
first need to generate these files with:

    $ ./autogen.sh

This only has to be done once.

Note:
Source package distributions do contain generated scripts, so this part
can be skipped if you are working from a disttributed copy of the source code.

Configuring
-----------

If you retrieved the source code from a packaged source distribution, or if
you are working directory from the repository and ran `autogen.sh`, then you
should have a `configure` script available.

    $ mkdir build
    $ cd build/
    $ ../configure --prefix=$PWD/install

Note: Running `configure` from within the source tree is not recommended as
it will pollute your source directory.

Building
--------

Building is performed with `make`.

    $ make
    $ make check

Debug & release builds
----------------------

Providing `CFLAGS` and `LDFLAGS` for debug/release builds can be tedious. For
convenience, a `build/release` and `build/debug` directory are provided, which
both contain a simple shell script to create a sensible configuration.

    $ cd build/release
    $ ./configure
    $ make
    $ make check
    $ make install

    $ cd build/debug
    $ ./configure
    $ make
    $ make check
    $ make install

Distributing
------------

Creating a release should only be done with in in-source build.

    $ ./configure
    $ make distcheck

This should produce a `{{ cookiecutter.project_slug }}-1.0.0.tar.gz` source
distribution archive.

Usage
-----

Once installed, the recommended procedure to include and link against
`{{ cookiecutter.project_slug }}` is the use of `pkg-config`.

    $ gcc program.c -o program.o $(pkg-config --cflags --libs {{ cookiecutter.project_slug }})

For this to work, make sure that `${prefix}/lib/pkgconfig` is in your
`PKG_CONFIG_PATH` environment variable. That should be the case if you
installed `{{ cookiecutter.project_slug }}` is a standard location.

Dependencies
------------

None

Authors
-------
- {{ cookiecutter.author }} <{{ cookiecutter.email }}>

Licensed under MIT/X
--------------------
Copyright (C) {% now 'utc', '%Y' %} {{ cookiecutter.author }}

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies
of the Software, and to permit persons to whom the Software is furnished to do
so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
