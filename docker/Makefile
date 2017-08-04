# NOTE: make sure you are using GNU make
# https://www.gnu.org/software/make/#download

.SECONDEXPANSION:

.PHONY: default all el6-build el7-build el6-push el7-push

default:
	@echo
	@echo "Run 'make help' to see all targets"
	@echo "Run 'make vars' to see variables"

all: build_el6 build_el7 push_el6 push_el7

build_el6:
	@echo Building el6 rpmbuilder containers
	docker build --pull --tag docker.io/jsosic/rpmbuilder:el6    rpmbuilder:el6
	docker build --tag docker.io/jsosic/rpmbuilder:el6ius rpmbuilder:el6ius

build_el7:
	@echo Building el7 rpmbuilder containers
	docker build --pull --tag docker.io/jsosic/rpmbuilder:el7    rpmbuilder:el7
	docker build --tag docker.io/jsosic/rpmbuilder:el7ius rpmbuilder:el7ius

push_el6:
	@echo Pushing el6 rpmbuilder containers
	docker push docker.io/jsosic/rpmbuilder:el6
	docker push docker.io/jsosic/rpmbuilder:el6ius

push_el7:
	@echo Pushing el7 rpmbuilder containers
	docker push docker.io/jsosic/rpmbuilder:el7
	docker push docker.io/jsosic/rpmbuilder:el7ius

help:
	@echo List of all accessible tasks
	@echo ------------------------------------
	@grep -B1 --color=never '^#\|^[a-z-]\+:' Makefile | sed '/^--$$/d'
