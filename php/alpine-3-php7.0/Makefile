NAME = phalconphp/php
VERSION = alpine-php7.0
ALIAS_1 = alpine-php7
ALIAS_2 = alpine-3-php7
SHELL = /bin/bash

.PHONY: pre-build docker-build post-build clean build release push tag do-push post-push

build: pre-build docker-build post-build

pre-build:
	tar -cvf installers.tar installers

post-build: clean

docker-build:
	docker build -t $(NAME):$(VERSION) --no-cache --rm .

release: build tag push

push: do-push post-push

tag:
	docker tag $(NAME):$(VERSION) $(NAME):$(ALIAS_1)
	docker tag $(NAME):$(VERSION) $(NAME):$(ALIAS_2)

do-push:
	docker push $(NAME):$(VERSION)
	docker push $(NAME):$(ALIAS_1)
	docker push $(NAME):$(ALIAS_2)

post-push:

clean:
	rm -f installers.tar

# vim:ft=make:noet:ci:pi:sts=0:sw=4:ts=4:tw=78:fenc=utf-8:et
