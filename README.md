# Docker_study
For the first time to use docker

Reference:https://peihsinsu.gitbooks.io/docker-note-book/content/docker-build.html

## Useage:
``$ docker build [Dockerfile] .``

## SSH into container
openssh-server is included in dockerfile

- port forwarding
``docker run -p [ip]:[hostPort]:[containerPort] [image name]``---->将container port mapping到host的port上
``docker run -P [image name]``---->放在ramdom port

    E.X. docker run -p 127.0.0.1:50001:22 redis
 
## Stop container
``$ docker kill [container id]``

## Docker repository rename
``$ docker tag [image id] [new repository name]``

## After build from dockefile
we need 

``mininet``
``openvswitch(OVS)`` 
``ryu`` 

let's get to work!

## Mininet
At this part ,things get pretty easy ,just ``apt-get install mininet``

## Openvswitch (OVS)
This one can takes times :
1. setup pre-ENV
```
apt-get install git

apt-get install autoconf automake libtool

apt-get install openssl

apt-get install libssl-dev

apt-get install make

apt-get install make-guile

apt-get install python-six (Python 3 or 2.7 are required )
```
2. clone ovs source code
``git clone https://github.com/openvswitch/ovs.git``

3. build the source code
```
cd ovs

./boot.sh

./configure

make

make check  //run ovs self-check, This can takes thousand of time.

make install
```

4. check if sucessed & set ENV
`` /sbin/lsmod | grep openvswitch``
``export PATH=$PATH:/usr/local/share/openvswitch/scripts``

5. Start up & test
``ovs-ctl start``

## Ryu controller
1. setup pre-request
`` sudo apt-get install python-pip python-dev build-essential``

2. setup dependency
``sudo apt-get install python-eventlet python-routes python-webob python-paramiko``

3. install ryu
``pip install ryu``

#####   *p.s if system warn about*
``locale.Error: unsupported locale setting``
##### Solution: 
``locale``-->``export LC_ALL=C``



# All done here!!
