FROM openshift/jenkins-slave-base-centos7

MAINTAINER Oleg Matskiv <omatskiv@redhat.com>

RUN yum clean all && \
    yum -y install openssh-server \
    yum -y install epel-release && \
    yum -y install PyYAML python-jinja2 python-httplib2 python-keyczar python-paramiko python-setuptools git python-pip
RUN mkdir /etc/ansible/
RUN echo -e '[local]\nlocalhost' > /etc/ansible/hosts
RUN echo -e '\nssh:localhost:allow\nsshd:localhost:allow' >> /etc/hosts.allow
RUN iptables -A INPUT -p tcp --dport ssh -j ACCEPT
RUN pip install ansible
