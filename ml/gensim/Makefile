
build-alpine:
	docker build -f Dockerfile.alpine -t gensim:alpine .

tag-alpine:
	docker tag gensim:alpine 2jason/gensim:alpine

push-alpine: tag-alpine
	docker push 2jason/gensim:alpine

