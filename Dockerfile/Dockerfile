#source image(made a mistake before by using ``ubuntu``)
FROM ubuntu:16.04

#setting ENV and installing request software
RUN apt-get update && apt-get install -y openssh-server \
    net-tools iputils-ping git vim curl wget

#for sshd setting
RUN mkdir /var/run/sshd

# set password of root to taku1994
RUN echo 'root:taku1994' | chpasswd

RUN sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

# SSH login fix. Otherwise user is kicked off after login
RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd

ENV NOTVISIBLE "in users profile"
RUN echo "export VISIBLE=now" >> /etc/profile

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
#CMD ["service ssh start"]
