############################################################
# Dockerfile to build MongoDB container images
# Based on Ubuntu
############################################################
# Set the base image to Ubuntu
FROM ubuntu
# File Author / Maintainer
MAINTAINER basedockerfile Pinghailinfeng
# Update the repository sources list
RUN echo "deb http://mirrors.163.com/ubuntu/ precise main restricted universe multiverse" > /etc/apt/sources.list
RUN apt-get update
# install openssh 
RUN apt-get install -y openssh-server
RUN mkdir -p /var/run/sshd
RUN mkdir -p /root/.ssh
# cancle pam restrictions
RUN sed -ri 's/session required    pam_loginuid.so/#session  required pam_loginuid.so/g' /etc/pam.d/sshd
# copy config file to right place ,give runnable script rights
ADD authorized_keys /root/.ssh/authorized_keys
ADD run.sh /run.sh
RUN chmod 755 /run.sh

#expose port
EXPOSE 22
#set run script
CMD ["/run.sh"]  
