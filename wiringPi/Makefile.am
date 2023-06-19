@SET_MAKE@

COFLAGS=-z+05:30
ACLOCAL_AMFLAGS=-I m4
DEFS=@DEFS@ -g -I. -I../devLib

include_HEADERS	= ads1115.h bmp180.h drcNet.h drcSerial.h ds18b20.h htu21d.h max31855.h \
				  max5322.h mcp23008.h mcp23016.h mcp23016reg.h mcp23017.h mcp23s08.h \
				  mcp23s17.h mcp23x0817.h mcp23x08.h mcp3002.h mcp3004.h mcp3422.h \
				  mcp4802.h pcf8574.h pcf8591.h pseudoPins.h rht03.h sn3218.h softPwm.h \
				  softServo.h softTone.h sr595.h wiringPi.h wiringPiI2C.h wiringPiSPI.h \
				  wiringSerial.h wiringShift.h wpiExtensions.h

COMMONSOURCES = wiringPi.c wiringSerial.c wiringShift.c piHiPri.c piThread.c wiringPiSPI.c \
				wiringPiI2C.c softPwm.c softTone.c mcp23008.c mcp23016.c mcp23017.c mcp23s08.c \
				mcp23s17.c sr595.c pcf8574.c pcf8591.c mcp3002.c mcp3004.c mcp4802.c mcp3422.c \
				max31855.c max5322.c ads1115.c sn3218.c bmp180.c htu21d.c ds18b20.c rht03.c \
				drcSerial.c drcNet.c pseudoPins.c wpiExtensions.c
includedir=@prefix@/include/wiringPi

libwiringPi_LTLIBRARIES=libwiringPi.la
libwiringPi_la_SOURCES=$(COMMONSOURCES) 
libwiringPi_la_LDFLAGS = -version-info @DEVLIBVER@ -pie
libwiringPi_la_CXXFLAGS = -fPIE
libwiringPidir=@libdir@

LIBTOOL_DEPS = @LIBTOOL_DEPS@
libtool: $(LIBTOOL_DEPS)
	$(SHELL) ./config.status --recheck

install-data-local:
	$(mkinstalldirs) $(DESTDIR)@libdir@
	$(mkinstalldirs) $(DESTDIR)@prefix@/include/wiringPi
