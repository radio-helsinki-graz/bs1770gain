CFLAGS+=-Werror
CFLAGS+=-Wall
CFLAGS+=-Wformat
CFLAGS+=-Wpointer-arith
CFLAGS+=-Wcast-align
CFLAGS+=-Wcast-qual
CFLAGS+=-Wreturn-type
CFLAGS+=-Wextra
CFLAGS+=-Wstrict-prototypes
CFLAGS+=-Wno-unused-parameter
#CFLAGS+=-Wmissing-declarations
#CFLAGS+=-Wmissing-prototypes
#CFLAGS+=-Wno-unused-variable

CPPFLAGS+=-I$(top_srcdir)/libpbutil
CPPFLAGS+=-I$(top_srcdir)/lib1770-2
CPPFLAGS+=-I$(top_srcdir)/libffsox-2

#CFLAGS+=-g
#CFLAGS+=-ggdb
#LDFLAGS+=-static-libgcc
#LDFLAGS+=-static-libstdc++
if WIN32
LDFLAGS+=-municode
endif

FFMPEG_PREFIX=@FFMPEG_PREFIX@
SOX_PREFIX=@SOX_PREFIX@

FFSOX_AVUTIL_V=@FFSOX_AVUTIL_V@
FFSOX_SWRESAMPLE_V=@FFSOX_SWRESAMPLE_V@
FFSOX_AVCODEC_V=@FFSOX_AVCODEC_V@
FFSOX_AVFORMAT_V=@FFSOX_AVFORMAT_V@
FFSOX_LIBSOX_V=@FFSOX_LIBSOX_V@

SODIR=@SODIR@
SOLIB=@SOLIB@
LDFLAGS+=@BS1770GAIN_LDFLAGS@

BS1770GAIN_TOOLS_ALL=@BS1770GAIN_TOOLS_ALL@
BS1770GAIN_TOOLS_INSTALL=@BS1770GAIN_TOOLS_INSTALL@
BS1770GAIN_TOOLS_UNINSTALL=@BS1770GAIN_TOOLS_UNINSTALL@

bin_PROGRAMS=
bin_PROGRAMS+=bs1770gain
bs1770gain_SOURCES=
bs1770gain_SOURCES+=bs1770gain.c
bs1770gain_LDADD=
bs1770gain_LDADD+=libbs1770gain.a
bs1770gain_LDADD+=$(top_builddir)/libffsox-2/libffsox_2.a
bs1770gain_LDADD+=$(top_builddir)/lib1770-2/lib1770_2.a
bs1770gain_LDADD+=$(top_builddir)/libpbutil/libpbutil.a
bs1770gain_LDADD+=-lm
#bin_PROGRAMS+=bs1770hello
#bs1770hello_SOURCES=
#bs1770hello_SOURCES+=bs1770hello.c
#bs1770hello_LDADD=
#bs1770hello_LDADD+=libbs1770gain.a
#bs1770hello_LDADD+=$(top_builddir)/libffsox-2/libffsox_2.a
#bs1770hello_LDADD+=$(top_builddir)/lib1770-2/lib1770_2.a
#bs1770hello_LDADD+=$(top_builddir)/libpbutil/libpbutil.a
#bs1770hello_LDADD+=-lm

noinst_LIBRARIES=libbs1770gain.a
libbs1770gain_a_SOURCES=
libbs1770gain_a_SOURCES+=bs1770gain.h
libbs1770gain_a_SOURCES+=bs1770gain_priv.h
libbs1770gain_a_SOURCES+=bs1770gain_print_xml.c
libbs1770gain_a_SOURCES+=bs1770gain_print_classic.c
libbs1770gain_a_SOURCES+=bs1770gain_aggregate.c
libbs1770gain_a_SOURCES+=bs1770gain_album.c
libbs1770gain_a_SOURCES+=bs1770gain_opath.c
libbs1770gain_a_SOURCES+=bs1770gain_parse_time.c
libbs1770gain_a_SOURCES+=bs1770gain_transcode.c
libbs1770gain_a_SOURCES+=bs1770gain_tree.c

OBJECTS=
OBJECTS+=$(bst1770gain_OBJECTS)
OBJECTS+=$(libbs1770gain_a_OBJECTS)
$(OBJECTS): $(CONFIG_HEADER)
$(OBJECTS): $(top_srcdir)/libpbutil/pbutil.h
$(OBJECTS): $(top_srcdir)/libpbutil/pbutil_priv.h
$(OBJECTS): $(top_srcdir)/lib1770-2/lib1770.h
$(OBJECTS): $(top_srcdir)/libffsox-2/ffsox.h
$(OBJECTS): $(top_srcdir)/libffsox-2/ffsox_priv.h
$(OBJECTS): $(top_srcdir)/libffsox-2/ffsox_dynload.h

all: $(BS1770GAIN_TOOLS_ALL)
install-exec-local: $(BS1770GAIN_TOOLS_INSTALL)
uninstall-local: $(BS1770GAIN_TOOLS_UNINSTALL)

.PHONY: bs1770gain-tools-nop
bs1770gain-tools-nop:

.PHONY: bs1770gain-tools-all
bs1770gain-tools-all: bs1770gain-tools/$(call SOLIB,,avutil,$(FFSOX_AVUTIL_V))
bs1770gain-tools-all: bs1770gain-tools/$(call SOLIB,,swresample,$(FFSOX_SWRESAMPLE_V))
bs1770gain-tools-all: bs1770gain-tools/$(call SOLIB,,avcodec,$(FFSOX_AVCODEC_V))
bs1770gain-tools-all: bs1770gain-tools/$(call SOLIB,,avformat,$(FFSOX_AVFORMAT_V))
bs1770gain-tools-all: bs1770gain-tools/$(call SOLIB,lib,sox,$(FFSOX_LIBSOX_V))

.PHONY: bs1770gain-tools-install
bs1770gain-tools-install: $(bindir)/bs1770gain-tools/$(call SOLIB,,avutil,$(FFSOX_AVUTIL_V))
bs1770gain-tools-install: $(bindir)/bs1770gain-tools/$(call SOLIB,,swresample,$(FFSOX_SWRESAMPLE_V))
bs1770gain-tools-install: $(bindir)/bs1770gain-tools/$(call SOLIB,,avcodec,$(FFSOX_AVCODEC_V))
bs1770gain-tools-install: $(bindir)/bs1770gain-tools/$(call SOLIB,,avformat,$(FFSOX_AVFORMAT_V))
bs1770gain-tools-install: $(bindir)/bs1770gain-tools/$(call SOLIB,lib,sox,$(FFSOX_LIBSOX_V))

.PHONY: bs1770gain-tools-uninstall
bs1770gain-tools-uninstall:
	rm -f $(prefix)/$(bindir)/bs1770gain-tools/$(call SOLIB,lib,sox,$(FFSOX_LIBSOX_V))
	rm -f $(prefix)/$(bindir)/bs1770gain-tools/$(call SOLIB,,avformat,$(FFSOX_AVFORMAT_V))
	rm -f $(prefix)/$(bindir)/bs1770gain-tools/$(call SOLIB,,avcodec,$(FFSOX_AVCODEC_V))
	rm -f $(prefix)/$(bindir)/bs1770gain-tools/$(call SOLIB,,swresample,$(FFSOX_SWRESAMPLE_V))
	rm -f $(prefix)/$(bindir)/bs1770gain-tools/$(call SOLIB,,avutil,$(FFSOX_AVUTIL_V))

bs1770gain-tools/%: $(FFMPEG_PREFIX)/$(SODIR)/%
	@mkdir -p $(@D)
	cp $< $(@D)
bs1770gain-tools/%: $(SOX_PREFIX)/$(SODIR)/%
	@mkdir -p $(@D)
	cp $< $(@D)
$(bindir)/bs1770gain-tools/%: bs1770gain-tools/%
	@mkdir -p $(@D)
	cp $< $(@D)
