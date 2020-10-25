# docker-base
docker-compose for elasticsearch application


dev
====

code .


build image
===========

docker build -t docker-base-app:tag -f build-docker/app/Dockerfile .  


check image
===========

docker run --rm --name docker-base-app-test -p 127.0.0.1:80:80 docker-base-app:1.0


