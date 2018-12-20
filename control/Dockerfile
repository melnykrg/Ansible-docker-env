# Use an official Python runtime as a parent image
FROM ubuntu:latest

# Install python
RUN apt-get update && apt-get install software-properties-common -y \
      && apt-add-repository ppa:ansible/ansible -y \
      && apt-get update && apt-get install ansible python-pip -y \
      && rm -rf /var/lib/apt/lists/*
RUN apt-get update && apt-get install -y openssh-server python-pip

# Install python package
RUN pip install --upgrade pip==9.0.3 && pip install netaddr deepdiff


RUN mkdir /var/run/sshd
RUN echo 'root:screencast' | chpasswd
RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

# SSH login fix. Otherwise user is kicked off after login
RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd

ENV NOTVISIBLE "in users profile"
RUN echo "export VISIBLE=now" >> /etc/profile


# Setup SSH access for remote systems
RUN mkdir -p /root/.ssh/
RUN chmod 0700 /root/.ssh
COPY ssh/id_rsa /root/.ssh/id_rsa
RUN chmod 0600 /root/.ssh/id_rsa
COPY ssh/config /root/.ssh/config
RUN chmod 0600 /root/.ssh/config
EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
WORKDIR /var/ansible
