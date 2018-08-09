# Docker_study
For the first time to use docker

Reference:https://peihsinsu.gitbooks.io/docker-note-book/content/docker-build.html

## Useage:
``$ docker build [Dockerfile] .``

## SSH into container
openssh-server is included in dockerfile
(需要将sshd_config中注解拿掉（ROOT LOGIN和password验证）)
### port forwarding
``docker run -p [ip]:[hostPort]:[containerPort] [image name]``
``docker run -P [image name]``放在ramdom port
E.X. docker run -p 127.0.0.1:50001:22 redis
 
## Stop container
``$ docker kill [container id]``

## Docker repository rename
``$ docker tag [image id] [new repository name]``

## After build from dockefile
we need ``mininet``,``openvswitch(OVS)``,``ryu`` ,so let's get to work!

## mininet
At this part ,things get pretty easy ,just ``apt-get install mininet``

## openvswitch (OVS)
This one can takes times :
1:setup pre-ENV
```
apt-get install git

apt-get install autoconf automake libtool

apt-get install openssl

apt-get install libssl-dev

apt-get install make

apt-get install make-guile

apt-get install python-six 如果没有安装python，请先安装python 2.7 or 3
```
2:clone ovs source code
``git clone https://github.com/openvswitch/ovs.git``

3:build the source code
```
cd ovs

./boot.sh

./configure

make

make check  //检查是否能通过ovs自带的单元测试用例（可选）

make install
```

4:check if sucessed & set ENV
`` /sbin/lsmod | grep openvswitch``
``export PATH=$PATH:/usr/local/share/openvswitch/scripts``

5:Start up & test
``ovs-ctl start``

### Ryu controller
1:setup pre-request
`` sudo apt-get install python-pip python-dev build-essential``

2:setup dependency
``sudo apt-get install python-eventlet python-routes python-webob python-paramiko``

3:install ryu

p.s if system warn about ``locale.Error: unsupported locale setting``
    Solution: ``locale``-->``export LC_ALL=C``

``pip install ryu``

# OK
