# Copyright (c) 2013, NVIDIA CORPORATION.
#
# Permission is hereby granted, free of charge, to any person obtaining a
# copy of this software and/or associated documentation files (the
# "Materials"), to deal in the Materials without restriction, including
# without limitation the rights to use, copy, modify, merge, publish,
# distribute, sublicense, and/or sell copies of the Materials, and to
# permit persons to whom the Materials are furnished to do so, subject to
# the following conditions:
#
# The above copyright notice and this permission notice shall be included
# unaltered in all copies or substantial portions of the Materials.
# Any additions, deletions, or changes to the original source files
# must be clearly indicated in accompanying documentation.
#
# If only executable code is distributed, then the accompanying
# documentation must state that "this software is based in part on the
# work of the Khronos Group."
#
# THE MATERIALS ARE PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
# EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
# MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
# IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
# CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
# TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
# MATERIALS OR THE USE OR OTHER DEALINGS IN THE MATERIALS.

SUBDIRS = \
	GLX_dummy

noinst_HEADERS = test_utils.h

TESTS_ENVIRONMENT = \
	TOP_BUILDDIR=$(top_builddir) \
	ABS_TOP_BUILDDIR=$(abs_top_builddir)

TESTS = \
	init_test_env.sh \
	testglxgetprocaddress.sh \
	testglxmcbasic.sh \
	testglxmcloop.sh \
	testglxmcthreads.sh \
	testglxmclate.sh \
	testglxmcoldlink.sh \
	testglxgetclientstr.sh \
	testglxqueryversion.sh \
	testglxnscrthreads.sh \
	testpatchentrypoints.sh \
	fini_test_env.sh

# TODO: These tests depend on the x11glvnd server extension, which isn't used
# anymore. They need to be rewritten to use the GLX_EXT_libglvnd extension
# instead.
#TESTS += testx11glvndproto.sh
#TESTS += testglxnscreens.sh

EXTRA_DIST = $(TESTS)

check_PROGRAMS = \
	testglxgetprocaddress \
	testglxmakecurrent \
	testglxmakecurrent_oldlink \
	testglxgetclientstr \
	testglxqueryversion \
	testpatchentrypoints

#check_PROGRAMS += testx11glvndproto
#check_PROGRAMS += testglxnscreens
#
#testglxnscreens_SOURCES = \
#	$(top_srcdir)/src/util/glvnd_pthread.c \
#	testglxnscreens.c \
#	test_utils.c
#
#testglxnscreens_CFLAGS = -I$(top_srcdir)/$(X11GLVND_DIR) $(AM_CFLAGS)
#
#testglxnscreens_LDADD = -lX11
#testglxnscreens_LDADD += $(top_builddir)/src/GLX/libGLX.la
#testglxnscreens_LDADD += $(top_builddir)/src/OpenGL/libOpenGL.la
#testglxnscreens_LDADD += $(top_builddir)/src/util/libtrace.la
#testglxnscreens_LDADD += -lX11 -ldl $(top_builddir)/$(X11GLVND_DIR)/libx11glvnd_client.la

# The *_oldlink variant tests that linking against legacy libGL.so works

TESTGLXMAKECURRENT_SOURCES_COMMON = \
	testglxmakecurrent.c \
	test_utils.c

testglxmakecurrent_SOURCES = \
	$(TESTGLXMAKECURRENT_SOURCES_COMMON)

testglxmakecurrent_oldlink_SOURCES = \
	$(TESTGLXMAKECURRENT_SOURCES_COMMON)

testglxmakecurrent_oldlink_LDADD = -lX11 -ldl
testglxmakecurrent_oldlink_LDADD += $(top_builddir)/src/GL/libGL.la
testglxmakecurrent_oldlink_LDADD += $(top_builddir)/src/util/libglvnd_pthread.la
testglxmakecurrent_oldlink_LDADD += $(top_builddir)/src/util/libtrace.la

#testx11glvndproto_CFLAGS = -I$(top_srcdir)/$(X11GLVND_DIR)
#testx11glvndproto_LDADD = -lX11 $(top_builddir)/$(X11GLVND_DIR)/libx11glvnd_client.la

# Disable annoying "unused" errors
AM_CFLAGS =                                  \
	-Wno-error=unused-variable               \
	-Wno-error=unused-label                  \
	-I$(top_srcdir)/include                  \
	-I$(top_srcdir)/src/util                 \
	-I$(top_srcdir)/src/util/glvnd_pthread


testglxgetprocaddress_LDADD = -lX11
testglxgetprocaddress_LDADD += $(top_builddir)/src/GLX/libGLX.la

testglxmakecurrent_LDADD = -lX11 -ldl
testglxmakecurrent_LDADD += $(top_builddir)/src/GLX/libGLX.la
testglxmakecurrent_LDADD += $(top_builddir)/src/OpenGL/libOpenGL.la
testglxmakecurrent_LDADD += $(top_builddir)/src/util/libglvnd_pthread.la
testglxmakecurrent_LDADD += $(top_builddir)/src/util/libtrace.la

testglxgetclientstr_LDADD = -lX11
testglxgetclientstr_LDADD += $(top_builddir)/src/GLX/libGLX.la
testglxgetclientstr_LDADD += $(top_builddir)/src/OpenGL/libOpenGL.la
testglxgetclientstr_LDADD += $(top_builddir)/src/util/libtrace.la

testglxqueryversion_LDADD = -lX11
testglxqueryversion_LDADD += $(top_builddir)/src/GLX/libGLX.la
testglxqueryversion_LDADD += $(top_builddir)/src/OpenGL/libOpenGL.la

testpatchentrypoints_SOURCES = \
	testpatchentrypoints.c \
	test_utils.c

testpatchentrypoints_LDADD = -lX11 -ldl
testpatchentrypoints_LDADD += $(top_builddir)/src/GLX/libGLX.la
testpatchentrypoints_LDADD += $(top_builddir)/src/OpenGL/libOpenGL.la
testpatchentrypoints_LDADD += $(top_builddir)/src/util/libtrace.la
