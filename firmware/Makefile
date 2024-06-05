GIT_VERSION=$(shell git describe --tags --always --dirty)

.PHONY: all
all:
	virtualenv .venv
	.venv/bin/pip install -U esphome==2024.5.4 pillow==10.2.0

	echo $(GIT_VERSION)

	sed  's/GIT_VERSION_FIELD/$(GIT_VERSION)/g' dcbuddy.yml > dcbuddy_versioned.yml
	.venv/bin/esphome compile dcbuddy_versioned.yml
	rm dcbuddy_versioned.yml
	rm -rf output
	mkdir output
	cp .esphome/build/dcbuddy/.pioenvs/dcbuddy/firmware.bin output/dcbuddy.bin
	cp .esphome/build/dcbuddy/.pioenvs/dcbuddy/firmware-factory.bin output/dcbuddy-factory.bin
