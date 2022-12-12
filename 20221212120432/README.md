# Run arbitrary ansible roles without tags and main yaml

I find a simple ansible playbook that allows the running of single role
tasks from your ansible code base. This is useful when you don't want to
have a large number of arbitrary playbooks with random roles. The
playbook is :

```
---
- hosts: all
  remote_user: "{{remote_user|default('root')}}"
  roles:
  - '{{role}}'
```

where to use the playbook we run `ansible-playbook -l localhost -e
role=<role_name> runrole.yaml`
