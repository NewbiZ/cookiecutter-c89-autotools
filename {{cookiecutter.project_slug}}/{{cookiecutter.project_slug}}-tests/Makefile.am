# Copyright (C) {% now 'utc', '%Y' %} {{ cookiecutter.author }}
# 
# Permission is hereby granted, free of charge, to any person obtaining a copy
# of this software and associated documentation files (the "Software"), to deal
# in the Software without restriction, including without limitation the rights
# to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
# copies of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:
# 
# The above copyright notice and this permission notice shall be included in
# all copies or substantial portions of the Software.
# 
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.

AM_CPPFLAGS = \
	-I$(top_srcdir)/{{cookiecutter.project_slug}}-lib/include \
	-I$(top_builddir)/{{cookiecutter.project_slug}}-lib/include

AM_CFLAGS = \
	-Wpedantic \
	-W -Wall \
	-Werror \
	-Wformat-security \
	-Wformat=2 \
	-Wpointer-arith \
	-Winit-self \
	-Wcast-align \
	-Wlogical-op \
	-Wshadow \
	-fvisibility=hidden \
	-Wl,--discard-all \
	-Wl,--no-undefined \
	-std=c89

check_PROGRAMS = \
	test_dummy

#
# test_dummy
#
test_dummy_SOURCES = \
	$(top_srcdir)/{{ cookiecutter.project_slug }}-tests/test_dummy.c \
	$(top_srcdir)/{{ cookiecutter.project_slug }}-tests/test.h

test_dummy_LDADD = \
	$(top_builddir)/{{ cookiecutter.project_slug }}-lib/lib{{ cookiecutter.project_slug }}.la

TESTS = ${check_PROGRAMS}

MAINTAINERCLEANFILES = \
	Makefile.in

