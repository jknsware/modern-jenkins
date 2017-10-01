# images/jenkins-tools/Dockerfile
FROM modernjenkins/jenkins-base
MAINTAINER jason@jknsware.com

LABEL dockerfile_location=https://github.com/jknsware/modern-jenkins/tree/master/images/jenkins-tools/Dockerfile \
    image_name=modernjenkins/jenkins-tools \
    base_image=modernjenkins/jenkins-base

# Tools Version Info
ENV TERRAFORM_VERSION   = '0.10.4'
ENV TERRAGRUNT_VERSION  = 'v0.13.0'
ENV ANSIBLE_VERSION

# Install Terraform
RUN curl -L https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip | tar zxv -C /usr/share/tools \
    && sudo chmod +x /usr/share/tools/terraform

# Install Terragrunt
RUN curl -Lo https://github.com/gruntwork-io/terragrunt/releases/download/${TERRAGRUNT_VERSION}/terragrunt_linux_amd64 | tar zxv -C /urs/share/tools \
    && sudo chmod +x /usr/share/tools/terragrunt

# Install Ansible
# RUN yum install -y \
#     epel-release \
#     ansible \
#     && yum clean all

RUN yum install -y \
    PyYAML \
    libtomcrypt \
    libtommath \
    libyaml \
    make \
    openssl \
    python-babel \
    python-backports \
    python-backports-ssl_match_hostname \
    python-cffi \
    python-enum34 \
    python-httplib2 \
    python-idna \
    python-ipaddress \
    python-jinja2 \
    python-markupsafe \
    python-paramiko \
    python-passlib \
    python-ply \
    python-pycparser \
    python-setuptools \
    python-six \
    python2-crypto \
    python2-cryptography \
    python2-pyasn1 \
    sshpass \
    && yum clean all



# It's easy to get confused when just a volume is being used, so let's just keep
# the container alive for clarity. This entrypoint will keep the container
# running for... infinity!
ENTRYPOINT ["sleep", "infinity"]