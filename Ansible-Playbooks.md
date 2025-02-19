## Ansible Playbooks

[Ansible Playbooks](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_intro.html) offer a repeatable, reusable, simple configuration management and multi-machine deployment system, one that is well suited to deploying complex applications. Playbooks are expressed in [YAML](https://docs.ansible.com/ansible/latest/reference_appendices/YAMLSyntax.html) format with a minimum of syntax.
<br>

A playbook runs in order from top to bottom. Within each play, tasks also run in order from top to bottom. Playbooks with multiple ‘plays’ can orchestrate multi-machine deployments, running one play on your webservers, then another play on your database servers, then a third play on your network infrastructure, and so on. At a minimum, each play defines two things:

* the managed nodes to target, using a [pattern](https://docs.ansible.com/ansible/latest/inventory_guide/intro_patterns.html#intro-patterns).
* at least one task to execute.

## Run a playbook

To run a playbook, we can use the command:

```
ansible-playbook <NAME OF THE YAML FILE>
```
<br>

## Validating task using check mode and diff mode

## check mode

[check mode](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_checkmode.html#using-check-mode) is a simulation of a playbook andd can be used for validating configuration management playbooks that run on one node at a time. To run check mode, we can use the command:

```
ansible-playbook <NAME OF THE YAML FILE> --check
```
<br>

## diff mode

[diff mode](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_checkmode.html#using-diff-mode) or using the ```--diff``` option for ansible-playbook can be used alone or with ```--check```. When you run in diff mode, any module that supports diff mode reports the changes made or, if used with ```--check```, the changes that would have been made. Diff mode is most common in modules that manipulate files (for example, the template module) but other modules might also show ‘before and after’ information (for example, the user module).

To run diff mode, we can use the command:

````
ansible-playbook <NAME OF THE YAML FILE> --diff
````
<br>

## syntax check

[syntax check](https://ansible.readthedocs.io/projects/lint/rules/syntax-check/) is use to to verify and check YAML syntax and if any of these reports a syntax error, this stops any further processing of these files. To syntax check, we can use the command:

```
ansible-playbook --syntax-check <NAME OF THE YAML FILE>
```
<br>

## Lint

[Lint](https://ansible.readthedocs.io/projects/lint/) is a command-line tool for linting playbooks, roles and collections aimed toward any Ansible users. Its main goal is to promote proven practices, patterns and behaviors while avoiding common pitfalls that can easily lead to bugs or make code harder to maintain.

It is also supposed to help users upgrade their code to work with newer versions of Ansible. Due to this reason we recommend using it with the newest version of Ansible, even if the version used in production may be older.

To run lint, we can use the command:

```
ansible-lint <NAME OF THE YAML FILE>
```
<br>










