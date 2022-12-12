#  Useful ansible guard for playbooks

Sometimes ansible can be a little to powerful and can wipe out the
infrastructure that you weren't expecting. We can use a short yaml to
create a check before running the dangerous commands. The yaml is shown
below. This simple script will allow you to double check the hosts you
are running the playbooks against.

```yaml
# vim: set ft=yaml:
---
- hosts: all
  gather_facts: false
  tasks:
    - local_action:
        module: ansible.builtin.debug
        msg: 'Run affects {{ansible_play_hosts|length}} hosts'
      run_once: true

    - local_action:
        module: ansible.builtin.pause
        prompt: Confirm number of hosts affected
      register: prompt
      when: not ansible_check_mode

    - name: Verify number of affected hosts
      local_action:
        module: ansible.builtin.assert
        that:
          - '{{prompt.user_input|int}} == {{ansible_play_hosts|length}}'
        quiet: true
      run_once: true
      when: not ansible_check_mode
```

