---
date created: Sunday, January 17th 2021, 3:51:17 pm
date modified: Friday, January 2nd 2026, 9:22:56 am
tags:
  - ansible
  - automation
---

# ansible

## ad-hoc commands

execute a module ad-hoc on some/all hosts:

```shell
ansible -i inventory all -m ansible.builtin.shell -a "dpkg --list"
```

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

## secrets

### encrypt string in ansible

```shell
echo -n 'hello world' | ansible-vault encrypt_string --stdin-name "MY_SECRET_VAR"
```

### decrypt ansible vault string

#### decrypt string

just copy & paste your encrypted string with including newlines (**remove starting spaces**):

```shell
echo '$ANSIBLE_VAULT;1.1;AES256
30643961666330643038313536353439356366336361666165316535333861643032396664306634' | tr -d ' ' | ansible-vault decrypt && echo
```

#### decrypt from stdin with copy & paste

```shell
ansible-vault decrypt
```

when prompted, enter your vault password, paste the encrypted text in there, hit return and then

++ctrl+d++

Here's an example:

```shell
ansible-vault decrypt
Vault password:
Reading ciphertext input from stdin
$ANSIBLE_VAULT;1.1;AES256
34353264393230616132376432303361386162363339666531653135636466363039373037653137
3036616366343536326635343866333339313965613935310a636366663262663436636238626564
33663637353737333334653466363965323835393333666539323238373530376434383961333338
6262313937386666630a393933663137663238393561356665653033333439393866613865386234
3166
Decryption successful
hello world%
```
