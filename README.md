# docker-base
docker-compose for elasticsearch application


dev
====

code .


build image
===========

docker build -t docker-base-app:1.0 -f build-docker/app/Dockerfile .  
docker build -t docker-base-api:1.0 -f build-docker/api/Dockerfile .  


check image
===========

docker run --rm --name docker-base-app-test -p 127.0.0.1:80:80 docker-base-app:1.0
docker run --rm --name docker-base-api-test -p 127.0.0.1:80:8000 docker-base-api:1.0


