[![CI](https://github.com/de-it-krachten/ansible-role-munge/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-munge/actions?query=workflow%3ACI)


# ansible-role-munge

Install & configures munge
See https://dun.github.io/munge/ for more information


Platforms
--------------

Supported platforms

- CentOS 7
- CentOS 8
- Debian 10 (Buster)
- Debian 11 (Bullseye)
- Ubuntu 18.04 LTS
- Ubuntu 20.04 LTS



Role Variables
--------------
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
</pre></code>


Example Playbook
----------------

<pre><code>
- name: Converge
  hosts: all
  vars: null
  tasks:
    - name: Include role 'ansible-role-munge'
      include_role:
        name: ansible-role-munge
</pre></code>
