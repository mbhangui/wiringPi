@SET_MAKE@

COFLAGS=-z+05:30
ACLOCAL_AMFLAGS=-I m4
DEFS=@DEFS@ -g -I../devLib -I../wiringPi

gpiobindir=@prefix@/bin
gpiobin_PROGRAMS = gpio
man_MANS=gpio.1

gpio_SOURCES = gpio.c readall.c
gpio_LDFLAGS = $(LDFLAGS)
gpio_LDADD = ../devLib/libwiringPiDev.la ../wiringPi/libwiringPi.la -lpthread -lrt -lm -lcrypt
gpio_CPPFLAGS = $(CPPFLAGS) -fPIE
