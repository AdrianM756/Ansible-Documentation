## Ansible AWX

[Ansible AWX](https://github.com/ansible/awx) provides a web-based user interface, REST API, and task engine built on top of Ansible. It is one of the upstream projects for [Red Hat Ansible Automation Platform](https://www.redhat.com/en/technologies/management/ansible?sc_cid=7015Y000003t7aWQAQ).
<br>

## Installation

On this demo, we will be installing Ansible AWX on a Debian Machine.
<br>

Let's update our repository.
```
apt update -y
```
<br>

Next, install the required dependancies.
```
apt-get install apt-transport-https ca-certificates software-properties-common unzip gnupg2 curl git -y
```
<br>

Modify the sourcelist using ```nano```, then add the  following:
```
nano /etc/apt/sources.list
```
```
deb http://ppa.launchpad.net/ansible/ansible/ubuntu focal main
```
<br>

Next, add a GPG key.
```
apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 93C4A3FD7BB9C367
```
<br>

Then, update again our repository.
```
apt update -y
```
<br>

## Install Ansible and Docker CE

Install ```Ansible```. After the installation, check the version.
```
apt-get install ansible -y
```
```
ansible --version
```
<br>

Next, add the docker GPG key.
```
curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```
<br>

Add the docker repository on the ```/etc/apt/sources.list.d/docker.list```.
```
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian $(lsb_release -cs) stable" | tee /etc/apt/sources.list.d/docker.list
```
<br>

Next, install Docker CE. check the docker status after the installation.
```
apt-get update -y
```
```
apt-get install docker-ce -y
```
```
systemctl status docker
```
<br>

## Install Docker Compose and Dependencies

Download the docker compose binary using ```wget```.
```
wget https://github.com/docker/compose/releases/download/v2.27.0/docker-compose-linux-x86_64
```
<br>

Move the file to ```/usr/bin/docker-compose``` using the ```mv``` command.
```
mv docker-compose-linux-x86_64 /usr/bin/docker-compose
```
<br>

make the file executable.
```
chmod +x /usr/bin/docker-compose
```
<br>

Finally, check the docker compose version.
```
docker-compose version
```
<br>

## Install Node.js and NPM

Install ```Node.js``` and ```NPM```.
```
apt-get install nodejs npm -y
```
```
npm install npm --global
```
<br>

Next, install ```PIP``` and Other Dependencies.
```
apt-get install python3-pip git pwgen -y
```
<br>

Finally, istall the python module for docker compose.
```
pip3 install docker-compose==2.27.0
```
<br>

## Install Ansible AWX

Install ```ansible awx``` using ```wget``` command:
```
wget https://github.com/ansible/awx/archive/refs/tags/17.1.0.zip
```
<br>

Next, unzip the file using the ```unzip``` commmand:
```
unzip 17.1.0.zip
```
<br>

Next, navigate to the ```awx-17.1.0/installer/``` directory.
```
cd awx-17.1.0/installer/
```
<br>

Configure the ```invetory``` file using ```nano``` then add the following:
```
admin_user=admin
admin_password=password
secret_key=TjFaBrbF9MYTEHVmRZJEIY6AoK8PD5
```
<br>

Finally, run the AWX installer.
```
ansible-playbook -i inventory install.yml
```
<br>

Opem your browser, then Access the AWX Web Interface.
```
http://<your-server-ip>
```
<br>
