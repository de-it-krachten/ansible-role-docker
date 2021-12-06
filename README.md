[![CI](https://github.com/de-it-krachten/ansible-role-docker/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-docker/actions?query=workflow%3ACI)


# ansible-role-docker

Installs docker


Platforms
--------------

Supported platforms

- CentOS 7
- CentOS 8
- Ubuntu 18.04 LTS
- Ubuntu 20.04 LTS
- Debian 10 (Buster)
- Debian 11 (Bullseye)



Role Variables
--------------
<pre><code>
# repo definition and/or GPG file
docker:
  CentOS:
    repo_url: https://download.docker.com/linux/centos/docker-ce.repo
    gpg_key: https://download.docker.com/linux/centos/gpg
  RedHat:
    repo_url: https://download.docker.com/linux/centos/docker-ce.repo
    gpg_key: https://download.docker.com/linux/centos/gpg
  OracleLinux:
    repo_url: https://download.docker.com/linux/centos/docker-ce.repo
    gpg_key: https://download.docker.com/linux/centos/gpg
  Fedora:
    repo_url: https://download.docker.com/linux/fedora/docker-ce.repo
    gpg_key: https://download.docker.com/linux/fedora/gpg
  Debian:
    gpg_key: https://download.docker.com/linux/debian/gpg
  Ubuntu:
    gpg_key: https://download.docker.com/linux/ubuntu/gpg

# Should swarm be configured
docker_swarm: false

# API listen address
docker_api_listen_address: 127.0.0.1

# API listen port w/out TLS
docker_api_listen_port_notls: 2375

# API listen port w/ TLS
docker_api_listen_port_tls: 2376

# Install docker
docker_install: true
docker_daemon: {}
docker_daemon_options: {}

docker_api: false
docker_api_tls: false

# SSL keys
openssl_server_cacrt: /dev/null
openssl_server_key: /dev/null

# /etc/docker/daemon.json w/out TLS
docker_daemon_api_notls:
  debug: false
  tls: false
  hosts:
    - unix://
    - tcp://{{ docker_api_listen_address }}:{{ docker_api_listen_port_notls }}

# /etc/docker/daemon.json w/ TLS
docker_daemon_api_tls:
  debug: false
  tls: true
  tlscert: "{{ openssl_server_cacrt }}"
  tlskey: "{{ openssl_server_key }}"
  tlscacert: "{{ openssl_server_cacrt }}"
  hosts:
    - unix://
    - tcp://{{ docker_api_listen_address }}:{{ docker_api_listen_port_tls }}

# Pip package for 
docker_pip:
  - docker

# List of firewall ports
docker_firewall_ports: []

# List of services
docker_firewall_services: []

# Docker packages
docker_packages:
  - docker-ce
  - containerd.io

# Obsolete docker packages to be removed
docker_packages_remove:
  - docker
  - docker-client
  - docker-client-latest
  - docker-common
  - docker-latest
  - docker-latest-logrotate
  - docker-logrotate
  # - docker-selinux
  # - docker-engine-selinux
  - docker-engine
</pre></code>


Example Playbook
----------------

<pre><code>

- name: Converge
  hosts: all
  tasks:

    - name: "Include role 'ansible-role-docker'"
      include_role:
        name: "ansible-role-docker"
</pre></code>
