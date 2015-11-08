FROM fedora:rawhide
MAINTAINER feddock "feddock@hotmail.com"

RUN dnf update -y 2> /dev/null
RUN dnf install openssh-server -y
RUN dnf install xorg-x11-server-Xorg xorg-x11-xinit xorg-x11-drv-vesa -y 
RUN dnf install git unzip wget -y
RUN dnf install eclipse -y

RUN echo 'root:eclipse' | chpasswd

RUN sed 's/\#Port 22/Port 2222/' -i /etc/ssh/sshd_config
RUN ssh-keygen -t 'rsa' -P "" -f /etc/ssh/ssh_host_rsa_key
RUN ssh-keygen -t 'ecdsa' -P "" -f /etc/ssh/ssh_host_ecdsa_key
RUN ssh-keygen -t 'ed25519' -P "" -f /etc/ssh/ssh_host_ed25519_key

EXPOSE 2222

CMD ["/usr/sbin/sshd","-D"]

