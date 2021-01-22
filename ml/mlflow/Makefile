GIT_HASH = $(shell git rev-parse --short HEAD)
ifndef TAG  # if kwarg `TAG` not specified
    TAG = $(GIT_HASH)
endif

show-tag:
	echo $(TAG)


build:
	docker build -f Dockerfile -t mlflow:$(TAG) .

tag:
	docker tag mlflow:$(TAG) 2jason/mlflow:$(TAG)

push: tag
	docker push 2jason/mlflow:$(TAG)

