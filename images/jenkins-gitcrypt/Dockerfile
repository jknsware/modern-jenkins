# images/jenkins-gitcrypt/Dockerfile
FROM modernjenkins/jenkins-base
MAINTAINER jason@jknsware.com

LABEL dockerfile_location=https://github.com/jknsware/modern-jenkins/tree/master/images/jenkins-gitcrypt/Dockerfile \
      image_name=modernjenkins/jenkins-gitcrypt \
      base_image=modernjenkins/jenkins-base

ENV GCVERSION 0.5.0-2

RUN yum install -y \
   git \
   gcc-c++ \
   make \
   openssh \
   openssh-clients \
   openssl \
   openssl-dev \
   openssl-devel \
   && yum clean

RUN curl -L https://github.com/AGWA/git-crypt/archive/debian/$GCVERSION.tar.gz | tar zxv -C /var/tmp
RUN cd /var/tmp/git-crypt-debian-$GCVERSION && make && make install PREFIX=/usr/share/jenkins/ref/gitcrypt

WORKDIR /repo
VOLUME /repo

# It's easy to get confused when just a volume is being used, so let's just keep
# the container alive for clarity. This entrypoint will keep the container
# running for... infinity!
ENTRYPOINT ["sleep", "infinity"]