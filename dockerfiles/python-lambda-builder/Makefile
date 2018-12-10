NAME         := python-lambda-builder
REVISION     := $(shell git rev-parse --short HEAD)
ORIGIN       := $(shell git remote get-url origin | sed -e 's/^.*@//g')
RELEASE_TAGS := 0.0.1 $(REVISION)
TAGS         := $(REVISION)
REGISTRY     := index.docker.io
USER         := kanga333

.PHONY: build
build:
	@docker build \
		--build-arg GIT_REVISION=$(REVISION) \
		--build-arg GIT_ORIGIN=$(ORIGIN) \
		--build-arg IMAGE_NAME=$(REGISTRY)/$(USER)/$(NAME) \
		$(addprefix -t $(REGISTRY)/$(USER)/$(NAME):,$(TAGS)) .

.PHONY: push
push:
	@for TAG in $(TAGS); do\
		docker push $(REGISTRY)/$(USER)/$(NAME):$$TAG; \
    done

.PHONY: release
release:
	@make build TAGS="$(RELEASE_TAGS)"
	@make push TAGS="$(RELEASE_TAGS)"
