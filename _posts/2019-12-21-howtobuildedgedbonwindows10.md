---
layout: post
title: How to Build edgedb on Windows 10
category: 03_Database
tag: [JavaScript]
---


![example](/assets/images/edgedb.jpg)



----

 
#### After Installation of DockerToolbox, follow as below;


- Pull edgedb

    - `$ docker pull edgedb/edgedb`

- Stop docker env first

    - `stop : $ docker-machine stop`

- Setting folder share

    - `share c: driver on VirtualBox setting if required.`

- Start docker env

    - `start: $ docker-machine start`

- Go to SHH to enjoy docker

    - go to `ssh : $ docker-machine ssh`

- Run Container
    - `docker run -d --name=edgedb-server -p "5656:5656" -p "8888:8888" -p "8889:8889" -v /c/dev:/var/lib/edgedb/data edgedb/edgedb`
- Go into Container Shell
    - `docker@default:~$ docker exec -it bd4 bash`




[https://www.w3schools.com/whatis/whatis_js.asp](https://www.w3schools.com/whatis/whatis_js.asp)
