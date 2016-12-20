FROM centos:7.3

RUN curl -o /tmp/epel.rpm https://www.mirrorservice.org/sites/dl.fedoraproject.org/pub/epel/7/x86_64/epel-release-7-3.noarch.rpm \
    && rpm -ivh /tmp/epel.rpm \
    && rm -f /tmp/epel.rpm \
    && yum install -y ansible

# Allow manual test runners a nice alias for running their playbook
RUN echo "alias 'run'='ansible-playbook -i inventory main.yml'" >> /root/.bashrc

ONBUILD ARG ROLE_NAME
ONBUILD COPY ./example /ansible/
ONBUILD COPY ./ /ansible/roles/${ROLE_NAME}

ONBUILD WORKDIR /ansible
ONBUILD ENTRYPOINT [ "ansible-playbook" ]
ONBUILD CMD [ "-i", "inventory", "main.yml" ]

ENTRYPOINT [ "ansible" ]
CMD [ "-v" ]
