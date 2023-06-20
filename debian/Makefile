all: debian.tar.gz wiringpi.dsc
version=$(shell cat ../conf-version)
arch=$(shell uname -m)
email=$(shell cat ../conf-email)

edit = sed \
	-e 's,@version\@,$(version),g' \
	-e "s,@release\@,"`cat ../conf-release`",g" \
	-e 's,@email\@,$(email),g' \
	-e 's,@prefix\@,$(prefix),g'

changelog: ../doc/ChangeLog Makefile ../conf-version ../conf-release \
../conf-email
	../catChangeLog --debian --name=wiringpi --state=stable \
		--urgency=low ../doc/ChangeLog > $@

control: control.in ../conf-email
	$(edit) $@.in > $@

copyright: copyright.in ../conf-email
	$(edit) $@.in > $@

wiringpi.dsc: wiringpi.dsc.in Makefile ../conf-version ../conf-release ../conf-email
	$(edit) $@.in > $@

clean:
	/bin/rm -f changelog control copyright wiringpi.dsc

debian.tar.gz: changelog compat control copyright libwiringpidev-dev.dirs \
libwiringpidev-dev.docs libwiringpidev-dev.install libwiringpi-dev.dirs \
libwiringpidev.dirs libwiringpi-dev.docs libwiringpidev.docs \
libwiringpi-dev.install libwiringpidev.install libwiringpi.dirs \
libwiringpi.docs libwiringpi.install README source/format \
wiringpi.install rules postinst postrm
	cd .. && tar cf - debian/changelog debian/compat debian/control \
		debian/copyright debian/libwiringpidev-dev.dirs \
		debian/libwiringpidev-dev.docs debian/libwiringpidev-dev.install \
		debian/libwiringpi-dev.dirs debian/libwiringpidev.dirs \
		debian/libwiringpi-dev.docs debian/libwiringpidev.docs \
		debian/libwiringpi-dev.install debian/libwiringpidev.install \
		debian/libwiringpi.dirs debian/libwiringpi.docs debian/libwiringpi.install \
		debian/README debian/source/format debian/rules \
		debian/wiringpi.install debian/postinst debian/postrm | gzip -c >debian/$@

