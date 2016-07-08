FROM ubuntu:xenial

RUN sed -i -e 's/exit\s\s*101/exit 0/' /usr/sbin/policy-rc.d

# init.
RUN sudo apt-get install -y curl git make ;\
      git clone https://github.com/voycey/cakephp-ansible.git cakephp-ansible;\
      cd cakephp-ansible ;\
      make init

ENV PLAYBOOK cakephp-ansible/setup.yml
RUN ansible-playbook-wrapper -vvv

VOLUME [ "/data" ]
