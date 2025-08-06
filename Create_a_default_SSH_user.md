## Create a default SSH user

Having a default SSH user ensures all target machines can be accessed uniformly. This avoids manually inputting different usernames per host in your inventory or playbooks or the need to specify ```--user``` or ```ansible_user``` in every playbook or command.
<br>

On this demo, we will create a default SSH user for ansible named ```adrian```. To Achieve this, we will need to the edit the file ```/etc/ansible/ansible.cfg``` using an editor:
```
nano /etc/ansible/ansible.cfg
```
<br>

Under the ```[defaults]``` section, add the ```remote_user = <DEFAULT SSH USER>```. For example:
```
[defaults]
remote_user = adrian
```
<br>

Once done, save and exit. We can check if the changes has take effect using these commands:
```
ansible all -m ping -v
```
<br>

Look for lines  indicating that it tries to connect as user ```adrian```.
<br>

