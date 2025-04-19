FROM debian:12

RUN mkdir -p /run/sshd

RUN apt-get update && apt-get install -y openssh-server sudo python3 && \
    rm -rf /var/lib/apt/lists/*

# Install SSH server and sudo
RUN apt-get update && apt-get install -y openssh-server sudo && \
    rm -rf /var/lib/apt/lists/*

# Create non-root user
RUN useradd -m -s /bin/bash ansible && \
    echo 'ansible ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers && \
    mkdir /home/ansible/.ssh && \
    chmod 700 /home/ansible/.ssh

# Configure SSH
COPY ssh-keys/id_rsa.pub /home/ansible/.ssh/authorized_keys
RUN chown -R ansible:ansible /home/ansible/.ssh && \
    chmod 600 /home/ansible/.ssh/authorized_keys && \
    sed -i 's/#PermitRootLogin yes/PermitRootLogin no/' /etc/ssh/sshd_config && \
    sed -i 's/#PasswordAuthentication yes/PasswordAuthentication no/' /etc/ssh/sshd_config

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]
