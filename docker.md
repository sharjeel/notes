Docker
===

Command:

`docker`

Search docker hub:

`docker search <string>`

Pull image:

`docker pull <string>`

Docker run:

`docker run <image> <command` e.g. `docker run learn/tutorial echo 'hello world'`

Installation within the docker container:

`docker run <image> apt-get install -y <package>` e.g. `docker run learn/tutorial apt-get install -y ping`

Find ID of the container:

`docker ps -l`

Save docker image changes:

`docker commit <id> [<repository>]`

e.g. 

`docker commit 698 learn/ping`

Inspect container:

`docker inspect <id>`

e.g. `docker inspect efe`

Upload changes to share with others on docker hub:

`docker push <repo>`

e.g. `docker push learn/ping`
