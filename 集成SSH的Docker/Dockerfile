FROM ubuntu:14.04
MAINTAINER etworker

# Update this time to run apt-get update if you want
ENV REFRESHED_AT 2016-01-26

# Will update if REFRESHED_AT updated
RUN apt-get -qq update

## Install necessary software
RUN apt-get install -y wget curl vim 

## Install ssh, add user admin:123456789
RUN apt-get install -y openssh-server
RUN mkdir -p /var/run/sshd
RUN mkdir -p /root/.ssh

RUN useradd -G adm,sudo,users -s /bin/bash -m admin && \
    echo 'admin:123456789' | chpasswd
RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd

## Environment variables
RUN echo " " >> /etc/profile && \
    echo "#_____________________" >> /etc/profile && \
    echo "force_color_prompt=yes" >> /etc/profile && \
    echo "alias cls='clear'" >> /etc/profile && \
    echo "alias u='cd ..'" >> /etc/profile && \
    echo "alias ll='ls -l'" >> /etc/profile && \
    echo "alias ins='sudo apt-get install -y'" >> /etc/profile && \
    echo "export TERM=linux" >> /etc/profile 

## Time Zone setting
RUN echo "Asia/Shanghai" > /etc/timezone && dpkg-reconfigure -f noninteractive tzdata

## Port, map to 8220-8225
EXPOSE   80
EXPOSE 8221
EXPOSE   22
EXPOSE  443
EXPOSE 8224
EXPOSE 8225

## run.sh
ADD run.sh /run.sh
RUN chmod 755 /run.sh
CMD [ "/run.sh" ]