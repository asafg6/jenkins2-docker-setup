FROM ubuntu:trusty
FROM golang

RUN apt-get update && apt-get -y upgrade && apt-get install -y openssh-server 
RUN sed -i 's|session    required     pam_loginuid.so|session    optional     pam_loginuid.so|g' /etc/pam.d/sshd
RUN mkdir -p /run/sshd
# install jdk for jenkins
RUN apt-get install -y openjdk-8-jdk
RUN adduser --quiet jenkins
RUN echo "jenkins:1234" | chpasswd
RUN mkdir -p /home/jenkins
USER root
RUN adduser jenkins sudo
RUN sed -i 's/#PermitRootLogin.*/PermitRootLogin no/' /etc/ssh/sshd_config
RUN sed -i 's/#RSAAuthentication.*/RSAAuthentication yes/' /etc/ssh/sshd_config
RUN sed -i 's/#PasswordAuthentication.*/PasswordAuthentication no/' /etc/ssh/sshd_config
RUN sed -i 's/#SyslogFacility.*/SyslogFacility AUTH/' /etc/ssh/sshd_config
RUN sed -i 's/#LogLevel.*/LogLevel INFO/' /etc/ssh/sshd_config
RUN sed -i 's/#PubkeyAuthentication.*/PubkeyAuthentication yes/' /etc/ssh/sshd_config
COPY id_rsa.pub /home/jenkins/.ssh/authorized_keys


EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]


