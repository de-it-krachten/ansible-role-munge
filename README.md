[![CI](https://github.com/de-it-krachten/ansible-role-munge/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-munge/actions?query=workflow%3ACI)


# ansible-role-munge

Install & configures munge
See https://dun.github.io/munge/ for more information


## Platforms

Supported platforms

- Red Hat Enterprise Linux 7<sup>1</sup>
- Red Hat Enterprise Linux 8<sup>1</sup>
- Red Hat Enterprise Linux 9<sup>1</sup>
- CentOS 7
- RockyLinux 8
- OracleLinux 8
- AlmaLinux 8
- AlmaLinux 9
- Debian 10 (Buster)
- Debian 11 (Bullseye)
- Ubuntu 18.04 LTS
- Ubuntu 20.04 LTS
- Ubuntu 22.04 LTS
- Fedora 35
- Fedora 36

Note:
<sup>1</sup> : no automated testing is performed on these platforms

## Role Variables
### defaults/main.yml
<pre><code>
# munge user & group
munge_user: munge
munge_group: munge

# munge packages by platform
munge_packages:
  RedHat:
    - munge
    - munge-libs
    - munge-devel
  Debian:
    - munge
    - libmunge-dev

# munge config + log directories
munge_dirs:
  - { path: /etc/munge, mode: '0755' }
  - { path: /var/log/munge, mode: '0755' }
  - { path: /var/run/munge, mode: '0755' }

# munge socket
munge_socket: /var/run/munge/munge.socket.2
munge_socket_owner: "{{ munge_user }}"
munge_socket_group: "{{ munge_group }}"
munge_socket_mode: "0660"
</pre></code>



## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'munge'
  hosts: all
  vars:
    munge_key: tests/munge.key
  tasks:
    - name: Include role 'munge'
      include_role:
        name: munge
</pre></code>
