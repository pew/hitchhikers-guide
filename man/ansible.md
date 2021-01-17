# ansible

## create lists

this is so annoying, please let me know if there's a better way.

**get ipv4 address from every host in playbook and put it into a list** to use it in an **ufw** rule

```yaml
- name: gather ipv4 addresses
  set_fact: ipv4="{% for host in ansible_play_hosts %}{{hostvars[host].ansible_default_ipv4.address}}{% if not loop.last %},{% endif %}{% endfor %}"

- name: set fact foo
  set_fact:
    foo: "{{ ipv4.split(',') }}"
    
- name: allow all access from all nodes
  ufw:
    rule: allow
    src: '{{ item }}'
  with_items:
    - "{{ foo }}"
```
