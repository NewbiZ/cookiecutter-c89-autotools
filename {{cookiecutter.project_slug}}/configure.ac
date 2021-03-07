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

# Start the configuration phase
# =============================
AC_PREREQ(2.59)

m4_define([AC_{{ cookiecutter.project_id }}_API_MAJOR], [1])
m4_define([AC_{{ cookiecutter.project_id }}_API_MINOR], [0])
m4_define([AC_{{ cookiecutter.project_id }}_API_PATCH], [0])
m4_define([AC_{{ cookiecutter.project_id }}_API_VERSION],
          [AC_{{ cookiecutter.project_id }}_API_MAJOR.AC_{{ cookiecutter.project_id }}_API_MINOR.AC_{{ cookiecutter.project_id }}_API_PATCH])

AC_DEFUN([AC_{{ cookiecutter.project_id }}_ABI_CUR], [0])
AC_DEFUN([AC_{{ cookiecutter.project_id }}_ABI_REV], [0])
AC_DEFUN([AC_{{ cookiecutter.project_id }}_ABI_AGE], [0])
AC_DEFUN([AC_{{ cookiecutter.project_id }}_ABI_VERSION],
         [AC_{{ cookiecutter.project_id }}_ABI_CUR:AC_{{ cookiecutter.project_id }}_ABI_REV:AC_{{ cookiecutter.project_id }}_ABI_AGE])

AC_INIT([{{ cookiecutter.project_slug }}], [AC_{{ cookiecutter.project_id }}_API_VERSION],
    [{{ cookiecutter.email }}], [{{ cookiecutter.project_slug }}],
    [{{ cookiecutter.url }}])

AM_INIT_AUTOMAKE([foreign subdir-objects])
LT_INIT

m4_ifdef([AM_SILENT_RULES], [
    AM_SILENT_RULES([yes])
])

AC_DEFINE({{ cookiecutter.project_id }}_API_MAJOR, AC_{{ cookiecutter.project_id }}_API_MAJOR, [{{ cookiecutter.project_name }} API major number])
AC_DEFINE({{ cookiecutter.project_id }}_API_MINOR, AC_{{ cookiecutter.project_id }}_API_MINOR, [{{ cookiecutter.project_name }} API minor number])
AC_DEFINE({{ cookiecutter.project_id }}_API_PATCH, AC_{{ cookiecutter.project_id }}_API_PATCH, [{{ cookiecutter.project_name }} API patch level])
AC_DEFINE({{ cookiecutter.project_id }}_API_VERSION, "AC_{{ cookiecutter.project_id }}_API_VERSION", [{{ cookiecutter.project_name }} API version])

AC_DEFINE({{ cookiecutter.project_id }}_ABI_CUR, AC_{{ cookiecutter.project_id }}_ABI_CUR, [{{ cookiecutter.project_name }} ABI current number])
AC_DEFINE({{ cookiecutter.project_id }}_ABI_REV, AC_{{ cookiecutter.project_id }}_ABI_REV, [{{ cookiecutter.project_name }} ABI revision number])
AC_DEFINE({{ cookiecutter.project_id }}_ABI_AGE, AC_{{ cookiecutter.project_id }}_ABI_AGE, [{{ cookiecutter.project_name }} ABI age number])
AC_DEFINE({{ cookiecutter.project_id }}_ABI_VERSION, "AC_{{ cookiecutter.project_id }}_ABI_VERSION", [{{ cookiecutter.project_name }} ABI version])

# Libtool
# =========
LTVER=AC_{{ cookiecutter.project_id }}_ABI_VERSION
AC_SUBST(LTVER)

# Check build tools
# =================
AC_PROG_CC
AC_LANG([C])
LT_INIT
AM_PROG_CC_C_O

# Documentation
# =============
AC_CHECK_PROG(HAVE_SPHINX, sphinx-build, yes, no)
if test "x$HAVE_SPHINX" = "xno"
then
    AC_MSG_WARN([Sphinx not found - documentation generation disabled])
fi
AM_CONDITIONAL([HAVE_SPHINX], [test "x$HAVE_SPHINX" = "xyes"])

# Dependencies
# ==================
AC_CONFIG_MACRO_DIR([m4])
PKG_PROG_PKG_CONFIG
PKG_INSTALLDIR

# Add pkg-config dependencies after this line
#AX_PKG_CHECK_MODULES([],[],[])

# Finish the configuration phase
# ==============================
AC_CONFIG_FILES([Makefile \
                 {{ cookiecutter.project_slug }}-bin/Makefile \
                 {{ cookiecutter.project_slug }}-lib/Makefile \
                 {{ cookiecutter.project_slug }}-lib/{{ cookiecutter.project_slug }}.pc \
                 {{ cookiecutter.project_slug }}-tests/Makefile \
                 {{ cookiecutter.project_slug }}-docs/Makefile])
AC_CONFIG_HEADERS([config.h {{ cookiecutter.project_slug }}-lib/include/{{ cookiecutter.project_slug }}/{{ cookiecutter.project_slug }}.h])

AC_OUTPUT
