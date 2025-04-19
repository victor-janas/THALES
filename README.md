# **Prerequisites**:
It is necessary to generate a pair of SSH keys before running the docker and place them in the ssh-keys folder. To do this, you can use the command:
- $ ssh-keygen -t rsa -f ssh-keys/id_rsa -N ''

# **Launching**
To be able to launch the docker you must execute the following commands:

- $ sudo docker-compose build
- $ sudo docker-compose up

# **Verification**
To verify operation:
- check the NGINX server from http://localhost:8080 or via : $ curl -I http://localhost:8080
- check the SSH connection on port 2222 via : $ ssh -i ssh-keys/id_rsa -p 2222 ansible@localhost
- check ANSIBLE Deployment : $ sudo docker logs nomdudossier_ansible_controller_1

I hope that the project will suit you and we can move on!

