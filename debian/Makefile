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

debian.tar.gz: changelog compat control copyright libwiringPiDev-dev.dirs \
libwiringPiDev-dev.docs libwiringPiDev-dev.install libwiringPi-dev.dirs \
libwiringPiDev.dirs libwiringPi-dev.docs libwiringPiDev.docs \
libwiringPi-dev.install libwiringPiDev.install libwiringPi.dirs \
libwiringPi.docs libwiringPi.install README source/format \
WiringPi.install rules
	cd .. && tar cf - debian/changelog debian/compat debian/control \
		debian/copyright debian/libwiringPiDev-dev.dirs \
		debian/libwiringPiDev-dev.docs debian/libwiringPiDev-dev.install \
		debian/libwiringPi-dev.dirs debian/libwiringPiDev.dirs \
		debian/libwiringPi-dev.docs debian/libwiringPiDev.docs \
		debian/libwiringPi-dev.install debian/libwiringPiDev.install \
		debian/libwiringPi.dirs debian/libwiringPi.docs debian/libwiringPi.install \
		debian/README debian/source/format debian/rules \
		debian/WiringPi.install | gzip -c >debian/$@

