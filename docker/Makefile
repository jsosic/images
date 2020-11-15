# NOTE: make sure you are using GNU make
# https://www.gnu.org/software/make/#download

.SECONDEXPANSION:

.PHONY: default all build_el6 build_el7 build_el8 push_el6 push_el7 push_el8

default:
	@echo
	@echo "Run 'make help' to see all targets"
	@echo "Run 'make vars' to see variables"

all: clean build_el6 build_el7 build_el8 push_el6 push_el7 push_el8

clean:
	@echo Removing all rpmbuilder images
	docker rmi -f jsosic/rpmbuilder:el8    docker.io/jsosic/rpmbuilder:el8
	docker rmi -f jsosic/rpmbuilder:el7ius docker.io/jsosic/rpmbuilder:el7ius
	docker rmi -f jsosic/rpmbuilder:el7    docker.io/jsosic/rpmbuilder:el7
	docker rmi -f jsosic/rpmbuilder:el6ius docker.io/jsosic/rpmbuilder:el6ius
	docker rmi -f jsosic/rpmbuilder:el6    docker.io/jsosic/rpmbuilder:el6

build_el6:
	@echo Building el6 rpmbuilder images
	docker build --pull --tag docker.io/jsosic/rpmbuilder:el6    rpmbuilder:el6
	docker build --tag docker.io/jsosic/rpmbuilder:el6ius rpmbuilder:el6ius

build_el7:
	@echo Building el7 rpmbuilder images
	docker build --pull --tag docker.io/jsosic/rpmbuilder:el7    rpmbuilder:el7
	docker build --tag docker.io/jsosic/rpmbuilder:el7ius rpmbuilder:el7ius

build_el8:
	@echo Building el8 rpmbuilder images
	docker build --pull --tag docker.io/jsosic/rpmbuilder:el8    rpmbuilder:el8

push_el6:
	@echo Pushing el6 rpmbuilder images
	docker push docker.io/jsosic/rpmbuilder:el6
	docker push docker.io/jsosic/rpmbuilder:el6ius

push_el7:
	@echo Pushing el7 rpmbuilder images
	docker push docker.io/jsosic/rpmbuilder:el7
	docker push docker.io/jsosic/rpmbuilder:el7ius

push_el8:
	@echo Pushing el8 rpmbuilder images
	docker push docker.io/jsosic/rpmbuilder:el8

pull:
	@echo Pulling images
	docker pull docker.io/jsosic/rpmbuilder:el6
	docker pull docker.io/jsosic/rpmbuilder:el6ius
	docker pull docker.io/jsosic/rpmbuilder:el7
	docker pull docker.io/jsosic/rpmbuilder:el7ius
	docker pull docker.io/jsosic/rpmbuilder:el8

systemd: build_systemd push_systemd

build_systemd:
	@echo Building systemd images
	docker build --pull --tag docker.io/jsosic/systemd:el7 systemd:el7
	docker build --pull --tag docker.io/jsosic/systemd:f29 systemd:f29
	docker build --pull --tag docker.io/jsosic/systemd:u1804 systemd:u1804

push_systemd:
	@echo Pushing systemd images
	docker push docker.io/jsosic/systemd:el7
	docker push docker.io/jsosic/systemd:f29
	docker push docker.io/jsosic/systemd:u1804

pull_systemd:
	@echo Pulling systemd images
	docker pull docker.io/jsosic/systemd:el7
	docker pull docker.io/jsosic/systemd:f29
	docker pull docker.io/jsosic/systemd:u1804

help:
	@echo List of all accessible tasks
	@echo ------------------------------------
	@grep -B1 --color=never '^#\|^[a-z-]\+:' Makefile | sed '/^--$$/d'
