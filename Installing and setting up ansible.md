## Ansible

[Ansible](https://www.redhat.com/en/ansible-collaborative/how-ansible-works) is an open source, command-line automation software application that is written in Python. It can configure systems, deploy software, and control workflows to support application deployment, system updates, and more.

## Setting up Ansible

On this Documentation, We will be installing **Ansible** on a Ubuntu machine.

To install Ansible on the Ubuntu machine, we will be using the command:

```
apt install ansible -y
```

The ``-y`` parameter answers yes to prompts without interrupting the process. to check the other options and syntax of ```apt```, you can visit this [link](https://phoenixnap.com/kb/apt-linux) for more info.

To verify the version, use the command:
```
ansible --version
```
To check how many modules you have, use the command:

```
ansible-doc -l | wc -l
```
To check other available parameter of ```ansible-doc```, you ca use the:

```
ansible-doc --help
```

## Setting up a host file

Ansible automate its tasks on managed nodes or “hosts” in your infrastructure by using a list or group of lists known as [inventory](https://docs.ansible.com/ansible/latest/inventory_guide/intro_inventory.html).

Under the ``/etc/ansible`` directory, create a yaml file named ```hosts```.

Inside the ```hosts``` we can add and specify the list of things that we are going to control.(Router, Switches, Servers, etc.) For this one, we will be using a simple example:

```
[servers]
<HOSTNAME/IP ADDRESS OF THE DEVICE>
```

Under the ```[servers]``` we input the list of devices that we want to control.

## Checking the connectivity

To verify the connectivity to all the host, we will be using the command:

```
ansible servers -m ping
```
Alternatively, we can use the command:

```
ansible servers -i /etc/hosts -m ping
```

```-i``` represents  the inventory in wich case is the ```/etc/hosts``` file. 

```servers``` represents the the devices that are inside of the ```[servers]``` inventory in the  ```/etc/hosts``` file.

```-m``` represents the module that we will be using in which case, we will be using [ping module](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/ping_module.html).
<br>
<br>
## Author:
[Sef Adrian Milambiling](https://github.com/AdrianM756)
