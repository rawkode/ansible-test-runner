FROM centos:6.7

RUN curl -o /tmp/epel.rpm https://www.mirrorservice.org/sites/dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm \
    && rpm -ivh /tmp/epel.rpm \
    && rm -f /tmp/epel.rpm \
    && yum install ansible

ONBUILD COPY ./example /ansible-role
ONBUILD COPY ./* /ansible-role/

ONBUILD WORKDIR /ansible-role
ONBUILD ENTRYPOINT [ "ansible-playbook -i example/inventory example/example.yml" ]

ENTRYPOINT [ "ansible" ]
CMD [ "-v" ]

