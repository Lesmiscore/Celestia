SUBDIRS = res

bin_PROGRAMS = celestia
INCLUDES = -I..

DEFS = -DCONFIG_DATA_DIR='"$(PKGDATADIR)"' -DLOCALEDIR='"$(datadir)/locale"' @DEFS@

if ENABLE_KDE
SUBDIRS += kde
celestiaKDELIBS = $(LIB_QT) $(LIB_KDECORE) $(LIB_KDEUI) $(LIB_KFILE) \
                  $(LIBSOCKET) kde/libkdegui.a
celestia_LDFLAGS = $(all_libraries) $(KDE_RPATH)
endif

if ENABLE_GTK
SUBDIRS += gtk
celestiaGTKLIBS = gtk/libgtkgui.a
endif

COMMONSOURCES = \
	celestiacore.cpp \
	configfile.cpp \
	destination.cpp \
	eclipsefinder.cpp\
	favorites.cpp \
	imagecapture.cpp \
	url.cpp

WINSOURCES = \
	avicapture.cpp \
	ODMenu.cpp \
	wglext.cpp \
	winbookmarks.cpp \
	windatepicker.cpp \
	wineclipses.cpp \
	wingotodlg.cpp \
	winhyperlinks.cpp \
	winlocations.cpp \
	winmain.cpp \
	winsplash.cpp \
	winssbrowser.cpp \
	winstarbrowser.cpp \
	wintime.cpp \
	wintourguide.cpp \
	winviewoptsdlg.cpp

if ENABLE_CELX
CELXSOURCES = celx.cpp
endif

if ENABLE_GLUT
GLUTSOURCES = glutmain.cpp
endif

if ENABLE_THEORA
THEORASOURCES = oggtheoracapture.cpp
endif

celestia_SOURCES = $(COMMONSOURCES) $(CELXSOURCES) $(GLUTSOURCES) $(THEORASOURCES)

EXTRA_DIST = \
	Celestia.dsp \
	celestia.mak \
	$(WINSOURCES)

celestia_LDADD = \
	$(celestiaKDELIBS) \
	$(celestiaGTKLIBS) \
	../celengine/libcelengine.a \
	../celtxf/libceltxf.a \
	../cel3ds/libcel3ds.a \
	../celmath/libcelmath.a \
	../celutil/libcelutil.a \
	$(SPICELIB)

noinst_HEADERS = $(wildcard *.h)
noinst_DATA = ../../celestia
CLEANFILES = ../../celestia

../../celestia: celestia
	(cd ../..; ln -s src/celestia/celestia)