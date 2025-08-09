## Ansible AWX

[Ansible AWX](https://github.com/ansible/awx) provides a web-based user interface, REST API, and task engine built on top of Ansible. It is one of the upstream projects for [Red Hat Ansible Automation Platform](https://www.redhat.com/en/technologies/management/ansible?sc_cid=7015Y000003t7aWQAQ).

On this demo, we will be installing Ansible AWX on a Debian Machine.
<br>

## Installation
First, Let update and upgrade our repository
```
sudo apt update && sudo apt -y full-upgrade
```
<br>

Next,install the neccessary dependencies.
```
sudo apt install apt-transport-https ca-certificates software-properties-common curl git gnupg2 unzip -y
```
<br>

Install Ansible and add the Ansible repository.
```
echo "deb http://ppa.launchpad.net/ansible/ansible/ubuntu focal main" | sudo tee /etc/apt/sources.list.d/ansible.list
```
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 93C4A3FD7BB9C367
```
```
sudo apt update -y
```
```
sudo apt install ansible -y
```
<br>

Install Docker and Docker Compose.
```
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```
```
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list
```
```
sudo apt update -y
```
```
sudo apt install docker-ce docker-ce-cli containerd.io docker-compose-plugin -y
```
<br>

Initially, acquire the Docker Compose binary from the Git repository by executing this command:
```
wget https://github.com/docker/compose/releases/download/v2.27.0/docker-compose-linux-x86_64
```
<br>

Transfer the downloaded binary to the /usr/bin/ directory:
```
mv docker-compose-linux-x86_64 /usr/bin/docker-compose
```
<br>
Next, set the executable permission to the docker-compose binary:
```
chmod +x /usr/bin/docker-compose
```
<br>

Install ```Node.js``` and ```NPM``` with the following command:
```
apt-get install nodejs npm -y
```
```
npm install npm --global
```
<br>

Set up ```PIP``` and other dependencies.
```
apt-get install python3-pip git pwgen -y
```
```
pip3 install docker-compose==2.27.0
```
<br>

Fetch the Ansible AWX from the GitHub repository by executing the subsequent command:
```
wget https://github.com/ansible/awx/archive/refs/tags/17.1.0.zip
```
<br>

Then, unzip the file.
```
unzip 17.1.0.zip
```
<br>

navigate to the extracted directory and create a secret key using the command provided below:
```
cd awx-17.1.0/installer/
```
```
pwgen -N 1 -s 30
```
<br>

Then Edit the ```invetory``` file to customize your AWX deployment (e.g., admin credentials, ports).
```
admin_user=admin
admin_password=password
secret_key=TjFaBrbF9MYTEHVmRZJEIY6AoK8PD5
```
<br>
Save and close the file then run the Ansible playbook to install the Ansible AWX:

```
ansible-playbook -i inventory install.yml
```
<br>

Finally, Deploy AWX using this commands:
```
docker compose up -d
```
<br>

Open a browser then access the AWX Web Interface.
```
http://<your-server-ip>:<port>
```
<br>

***NOTE:*** The default port is usually port ```80``` or ```8052```, depending on your ```.env``` configuration.
<br>


Default port is usually ```80``` or 8052, depending on your .env configuration.

