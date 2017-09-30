# images/jenkins-tools/Dockerfile
FROM modernjenkins/jenkins-base
MAINTAINER jason@jknsware.com

LABEL dockerfile_location=https://github.com/jknsware/modern-jenkins/tree/master/images/jenkins-tools/Dockerfile \
    image_name=modernjenkins/jenkins-tools \
    base_image=modernjenkins/jenkins-base

# Tools Version Info
ENV TERRAFORM_VERSION   = '0.10.4'
ENV TERRAGRUNT_VERSION  = 'v0.13.0'

# Install Terraform
RUN curl -L https://releases.hashicorp.com/terraform/${_TERRAFORM_VERSION}/terraform_${_TERRAFORM_VERSION}_linux_amd64.zip | tar zxv -C /usr/share/terraform \
    && sudo chmod +x /usr/share/terraform/terraform



# Install Terragrunt
[ -f /var/tmp/terragrunt-${_TERRAGRUNT_VERSION} ] || curl -Lo /var/tmp/terragrunt-${_TERRAGRUNT_VERSION} "https://github.com/gruntwork-io/terragrunt/releases/download/${_TERRAGRUNT_VERSION}/terragrunt_linux_amd64"
[ -f /var/tmp/terragrunt-${_TERRAGRUNT_VERSION} ] && sudo cp -f /var/tmp/terragrunt-${_TERRAGRUNT_VERSION} /usr/local/bin/terragrunt && sudo chmod +x /usr/local/bin/terragrunt
sudo ln -sf /usr/local/bin/terragrunt /usr/bin/terragrunt



# It's easy to get confused when just a volume is being used, so let's just keep
# the container alive for clarity. This entrypoint will keep the container
# running for... infinity!
ENTRYPOINT ["sleep", "infinity"]