# Using Ansible block function allows grouping tasks

In Ansible 2.0 and above you can join tasks together with a block level,
allowing multiple tasks to be run based on a conditional.

For example running

```
tasks:
  - block:
    - debug: msg='Task 1'
    - debug: msg='Task 2'
    - debug: msg='Task 3'
    when: ansible_distribution == 'Ubuntu'

```
This means the tasks only run if the system is ubuntu
