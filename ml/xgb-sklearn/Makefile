
build-slim:
	docker build -f Dockerfile.slim -t xgb-sklearn:slim .

tag-slim:
	docker tag xgb-sklearn:slim 2jason/xgb-sklearn:slim

push-slim: tag-slim
	docker push 2jason/xgb-sklearn:slim

