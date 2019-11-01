FROM centos:7

RUN yum -y install openssh-server

RUN useradd alver && \
    echo "1234" | passwd alver  --stdin && \
    mkdir /home/alver/.ssh && \
    chmod 700 /home/alver/.ssh

COPY remote-key.pub /home/alver/.ssh/authorized_keys

RUN chown alver:alver   -R /home/alver && \
    chmod 600 /home/alver/.ssh/authorized_keys

RUN /usr/sbin/sshd-keygen

CMD /usr/sbin/sshd -D
