# janus-docker
Debian based docker image for [Meetecho's Janus Gateway](https://github.com/meetecho/janus-gateway)

## Description
All the janus docker builds I have seen in hub.docker.com were all ubuntu based and/or of some redhat flavor. I successfully build janus in debian 7 and 8 before, so I thought it would be a good way to practice docker best practices and provide a debian based image at the same time.

For the automated build go to [hub.docker.com](https://hub.docker.com/r/mcroth/janus-docker/)

Many thanks for [meetecho](http://www.meetecho.com) for providing us [Janus Gateway](https://github.com/meetecho/janus-gateway)!

Docker best practices heavily inspired from [Damon Oehlman's ubuntu based docker image for janus](https://github.com/DamonOehlman/docker-janus).

## quickstart 
```
root@mcroth:~/sandbox# git clone https://github.com/krull/janus-docker.git
Cloning into 'janus-docker'...
remote: Counting objects: 51, done.
remote: Compressing objects: 100% (39/39), done.
remote: Total 51 (delta 12), reused 44 (delta 8), pack-reused 0
Unpacking objects: 100% (51/51), done.
Checking connectivity... done.
root@mcroth:~/sandbox# cd janus-docker/
root@mcroth:~/sandbox/janus-docker# docker-compose up -d
Creating network "janusdocker_front-tier" with driver "bridge"
Creating network "janusdocker_back-tier" with driver "bridge"
Pulling janus-gateway (mcroth/janus-docker:latest)...
latest: Pulling from mcroth/janus-docker
6a5a5368e0c2: Pull complete
c98cef4c208b: Pull complete
76dc1a643124: Pull complete
74cae242e22d: Pull complete
e299d71a0a74: Pull complete
19ef9eddff9c: Pull complete
bfa426fc5ba7: Pull complete
f2c856642d97: Pull complete
7074c35f0d15: Pull complete
724a1491bde8: Pull complete
618ceafccc5a: Pull complete
Digest: sha256:86f6921bb3cfdb52df25e4f4857660dd6a9abab69807cb2c2d5548756a4a1fab
Status: Downloaded newer image for mcroth/janus-docker:latest
Creating janus-gateway
root@mcroth:~/sandbox/janus-docker# docker ps -a
CONTAINER ID        IMAGE                 COMMAND                  CREATED             STATUS              PORTS                                            NAMES
63cd3bcf2a78        mcroth/janus-docker   "/opt/janus/bin/janus"   10 seconds ago      Up 8 seconds        0.0.0.0:8088->8088/tcp, 0.0.0.0:8188->8188/tcp   janus-gateway
root@mcroth:~/sandbox/janus-docker# 
```

A full set of default janus config files are in ./janus folder. 

## build criteria
```
DataChannels support:      yes
BoringSSL (no OpenSSL):    no
Recordings post-processor: yes
TURN REST API client:      yes
Doxygen documentation:     no
Transports:
    REST (HTTP/HTTPS):     yes
    WebSockets:            yes (new API)
    RabbitMQ:              no
    MQTT:                  no
    Unix Sockets:          yes
Plugins:
    Echo Test:             yes
    Streaming:             yes
    Video Call:            yes
    SIP Gateway:           yes
    Audio Bridge:          yes
    Video Room:            yes
    Voice Mail:            yes
    Record&Play:           yes
    Text Room:             yes
```
