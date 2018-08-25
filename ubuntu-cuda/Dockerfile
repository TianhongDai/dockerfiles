# from the nvidia cuda ubuntu-16.04-base, the minimum insall
FROM nvidia/cuda:9.0-base-ubuntu16.04
MAINTAINER Tianhong Dai tianhongdai914@gmail.com

# install the basic packages
RUN apt-get update && apt-get install -y \
    vim \
    tmux \
    bzip2 \
    wget \
    openssh-server

RUN mkdir /var/run/sshd
# change the password
RUN echo 'root:password' | chpasswd
# revise the ssh configure file
RUN sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config 
# SSH login fix. Otherwise user is kicked off after login
RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd
# ssh port
EXPOSE 22
# start the ssh service when the container is start
CMD ["/usr/sbin/sshd", "-D"]
