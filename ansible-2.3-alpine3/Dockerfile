FROM alpine:3.6

MAINTAINER Anton Ustyuzhanin <au@hellofresh.com>

COPY ./requirements.txt /tmp/requirements.txt

RUN apk --update add sudo && \
    apk --update add python py-pip openssl ca-certificates && \
    apk --update add --virtual build-dependencies python-dev libffi-dev openssl-dev build-base && \
    pip install -r /tmp/requirements.txt && \
    apk --update add sshpass openssh-client rsync

RUN pip install ansible==2.3.2.0 && \
    mkdir -p /etc/ansible && \
    echo 'localhost' > /etc/ansible/hosts


RUN apk del build-dependencies && \
    rm -rf /var/cache/apk/* /tmp/*

CMD [ "ansible-playbook", "--version" ]
