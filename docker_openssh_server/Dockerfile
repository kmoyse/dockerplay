### 1. Get Linux 20.04 (LTS)
FROM ubuntu:20.04

### 2. Get Java via the package manager
RUN apt-get update \
	&& apt-get upgrade -y \
	&& apt-get install -y openjdk-8-jre
	
RUN update-alternatives --list java
RUN java -version

### 3. SSHd 
RUN apt-get update \
	&& apt-get install -y openssh-server
RUN mkdir /var/run/sshd
RUN echo 'root:akigrafsoft' | chpasswd
RUN sed -i 's/#*PermitRootLogin prohibit-password/PermitRootLogin yes/g' /etc/ssh/sshd_config

# SSH login fix. Otherwise user is kicked off after login
RUN sed -i 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' /etc/pam.d/sshd

ENV NOTVISIBLE="in users profile"
RUN echo "export VISIBLE=now" >> /etc/profile

RUN useradd -ms /bin/bash akigrafsoft
RUN echo 'akigrafsoft:akigrafsoft' |chpasswd

RUN mkdir /home/akigrafsoft/.ssh

#WORKDIR /home/akigrafsoft/.ssh

COPY id_rsa.pub /home/akigrafsoft/.ssh/authorized_keys


EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
