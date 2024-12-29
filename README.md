[![CI](https://github.com/de-it-krachten/ansible-role-munge/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-munge/actions?query=workflow%3ACI)


# ansible-role-munge

Install & configures munge
See https://dun.github.io/munge/ for more information



## Dependencies

#### Roles
None

#### Collections
None

## Platforms

Supported platforms

- Red Hat Enterprise Linux 8<sup>1</sup>
- Red Hat Enterprise Linux 9<sup>1</sup>
- RockyLinux 8
- RockyLinux 9
- OracleLinux 8
- OracleLinux 9
- AlmaLinux 8
- AlmaLinux 9
- SUSE Linux Enterprise 15<sup>1</sup>
- openSUSE Leap 15
- Debian 11 (Bullseye)
- Debian 12 (Bookworm)
- Ubuntu 20.04 LTS
- Ubuntu 22.04 LTS
- Ubuntu 24.04 LTS
- Fedora 40
- Fedora 41

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
  Suse:
    - munge
    - libmunge2

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
  become: 'yes'
  vars:
    munge_key: tests/munge.key
  tasks:
    - name: Include role 'munge'
      ansible.builtin.include_role:
        name: munge
</pre></code>
