AUTOMAKE_OPTIONS = subdir-objects

if WANT_JANSSON
JANSSON_INCLUDES= -I$(top_srcdir)/compat/jansson
else
JANSSON_INCLUDES=
endif

EXTRA_DIST	= example-cfg.json nomacro.pl

SUBDIRS		= compat

bin_PROGRAMS	= minerd

dist_man_MANS	= minerd.1

minerd_SOURCES	= elist.h miner.h compat.h \
		  cpu-miner.cpp equihash/equihash.cpp util.cpp \
		  sha2.cpp
if USE_ASM
if ARCH_x86
minerd_SOURCES += sha2-x86.S
endif
if ARCH_x86_64
minerd_SOURCES += sha2-x64.S
endif
if ARCH_ARM
minerd_SOURCES += sha2-arm.S
endif
if ARCH_PPC
minerd_SOURCES += sha2-ppc.S
endif
endif
minerd_LDFLAGS	= $(PTHREAD_FLAGS)
minerd_LDADD	= @LIBCURL@ @JANSSON_LIBS@ @PTHREAD_LIBS@ @WS2_LIBS@ @SODIUM_LIBS@
minerd_CFLAGS	= -fno-strict-aliasing
minerd_CPPFLAGS	= @LIBCURL_CPPFLAGS@ $(JANSSON_INCLUDES) $(PTHREAD_FLAGS)
CC = gcc
CXX = g++
CCLD = g++
