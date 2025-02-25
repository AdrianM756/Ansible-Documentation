## Ansible Module

[Ansible module](https://www.redhat.com/en/topics/automation/what-is-an-ansible-module) is a small program that performs actions on a local machine, application programming interface (API), or remote host.

Modules are expressed as code, usually in Python, and contain metadata that defines when and where a specific automation task is executed and which users can execute it.

To check the list of all the current modules that are available on the system, we can use the command:
```
ansible-doc -l
```
<br>

Alternatively, to check it's offline version, we can use the command:
```
ansible-doc archive
```
<br>

## Ansible Ping

One of the commonly used module is [ansible ping](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/ping_module.html) It is commonly use to check the reachability and connectivity  of a host or inventory file. To check the connectivity from a hostfile using the command:
```
asible <HOSTNAME FROM THE INVENTORY FILE> -m ping
```
<br>

Alternatively, if your want to run ping to all the available host on the inventory file, we can run the command:
```
ansible all -m ping
```
<br>

However, if you want to specify a different invertory file, you can run the command:
```
asible -i <PATH OF THE INVENTORY FILE> -m ping
```
<br>




