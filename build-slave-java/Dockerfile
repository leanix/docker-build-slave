# This Dockerfile is used to build an image containing basic stuff to be used as a Jenkins slave build node.
FROM dockerfile/java:oracle-java7
MAINTAINER Andre Christ <andre.christ@leanix.net>

RUN apt-get update

# Install a basic SSH server
RUN apt-get install -y openssh-server
RUN sed -i 's|session    required     pam_loginuid.so|session    optional     pam_loginuid.so|g' /etc/pam.d/sshd
RUN mkdir -p /var/run/sshd

# Add user jenkins to the image
RUN adduser --quiet jenkins
# Set password for the jenkins user (you may want to alter this).
RUN echo "jenkins:jenkins" | chpasswd

RUN apt-get install -y maven

# Standard SSH port
EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]
