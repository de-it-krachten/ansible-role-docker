[![CI](https://github.com/de-it-krachten/ansible-role-docker/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-docker/actions?query=workflow%3ACI)


# ansible-role-docker

Installs & configures Docker CE

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
#-----------------------------------------
# Docker package repository
#-----------------------------------------

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
  Rocky:
    repo_url: https://download.docker.com/linux/centos/docker-ce.repo
    gpg_key: https://download.docker.com/linux/centos/gpg
  AlmaLinux:
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


#-----------------------------------------
# Docker OS settings
#-----------------------------------------

# Should cgroups v2 be enabled (Fedora only)
docker_cgroups_v2: false


#-----------------------------------------
# Docker networking
#-----------------------------------------

# Enable networking from container -> outsite-world
docker_networking_outbound: false

# Docker API  
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

# Pip package
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

### vars/family-RedHat.yml
<pre><code>
# OS release
docker_os_release: "{{ ansible_distribution_major_version }}"

# Docker CE packages
docker_packages:
  - docker-ce
</pre></code>

### vars/family-Debian.yml
<pre><code>
# OS release
docker_os_release: "{{ ansible_distribution_major_version }}"

# Docker CE packages
docker_packages:
  - docker-ce

# Docker URL 
docker_repo_url: https://download.docker.com/linux

# Docker release channel
docker_apt_release_channel: stable

# Docker architecture
docker_apt_arch: amd64

# Docker APT repostory
docker_apt_repository: >-
  deb [arch={{ docker_apt_arch }}] {{ docker_repo_url }}/{{ ansible_distribution | lower }}
  {{ ansible_distribution_release }} {{ docker_apt_release_channel }}

# APT key error ignore?
docker_apt_ignore_key_error: true

# APT GPG url
docker_apt_gpg_key: "{{ docker_repo_url }}/{{ ansible_distribution | lower }}/gpg"
</pre></code>



## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'docker'
  hosts: all
  vars:
  tasks:
    - name: Include role 'docker'
      include_role:
        name: docker
</pre></code>
