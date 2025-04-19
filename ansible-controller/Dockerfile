FROM almalinux:9

# Install Ansible and dependencies
RUN dnf install -y epel-release && \
    dnf install -y ansible openssh-clients && \
    dnf clean all

# Create Ansible user
RUN useradd -m -s /bin/bash ansible

# Copy configuration files
COPY --chown=ansible:ansible ansible-controller/ansible.cfg /home/ansible/.ansible.cfg
COPY --chown=ansible:ansible ansible-controller/inventory.ini /home/ansible/inventory.ini
COPY --chown=ansible:ansible ansible-controller/playbook.yml /home/ansible/playbook.yml
COPY --chown=ansible:ansible ssh-keys/id_rsa /home/ansible/.ssh/id_rsa

# Set permissions
RUN chmod 600 /home/ansible/.ssh/id_rsa

USER ansible
WORKDIR /home/ansible
