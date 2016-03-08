start jenkins docker
====================

`docker-compose up jenkins`

build image
===========

`docker build -t agileworks/jenkins-workshop .`

access running jenkins-workshop container
=========================================

`docker exec -it jenkins /bin/bash -l`

push image
----------

```
docker login
docker push agileworks/jenkins-workshop
```
