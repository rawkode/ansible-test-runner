FROM centos:6.7

RUN curl -o /tmp/epel.rpm https://www.mirrorservice.org/sites/dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm \
    && rpm -ivh /tmp/epel.rpm \
    && rm -f /tmp/epel.rpm \
    && yum install -y ansible

ONBUILD ARG ROLE_NAME
ONBUILD COPY ./example /ansible/
ONBUILD COPY ./ /ansible/roles/${ROLE_NAME}

ONBUILD WORKDIR /ansible
ONBUILD ENTRYPOINT [ "ansible-playbook -i inventory main.yml" ]

ENTRYPOINT [ "ansible" ]
CMD [ "-v" ]
