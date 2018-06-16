# How to run a container with tomcat and ansible:

# replace docker/ansible with your ssh private key
# replace docker/ansible.pub with your ssh public key
$ sudo docker build -t tomcat_webserver docker/

$ sudo docker run -d -p22:22 tomcat_webserver

#to get the container IPaddress
$ sudo docker inspect tomcat_webserver | jq ".[0].NetworkSettings.Networks.bridge.IPAddress"

# add ip address to /inventory/hosts/ Under [hosts-ansible] and then
$ ssh ansible@<IPAddress>

#it should looks like this, you're in: 
ansible@IPaddress $

# Then run ansible-playbook
$ ansible-playbook -i inventory/hosts tomcat-ansible.yml

