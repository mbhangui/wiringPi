@SET_MAKE@

COFLAGS=-z+05:30
ACLOCAL_AMFLAGS=-I m4
DEFS=@DEFS@ -g -I. -I../wiringPi

include_HEADERS	= ds1302.h gertboard.h lcd128x64.h lcd.h maxdetect.h \
				  piFace.h piGlow.h piNes.h scrollPhat.h
COMMONSOURCES =	ds1302.c maxdetect.c piNes.c gertboard.c piFace.c \
				lcd128x64.c lcd.c scrollPhat.c piGlow.c
includedir=@prefix@/include/wiringPiDev

libwiringPiDev_LTLIBRARIES=libwiringPiDev.la
libwiringPiDev_la_SOURCES=$(COMMONSOURCES) 
libwiringPiDev_la_DEPENDENCIES = ../wiringPi/libwiringPi.la
libwiringPiDev_la_LDFLAGS = -version-info @DEVLIBVER@ -pie -L../wiringPi
libwiringPiDev_la_LIBADD = -lwiringPi
libwiringPiDev_la_CXXFLAGS = -fPIE
libwiringPiDevdir=@libdir@

LIBTOOL_DEPS = @LIBTOOL_DEPS@
libtool: $(LIBTOOL_DEPS)
	$(SHELL) ./config.status --recheck

install-data-local:
	$(mkinstalldirs) $(DESTDIR)@libdir@
	$(mkinstalldirs) $(DESTDIR)@prefix@/include/wiringPiDev
