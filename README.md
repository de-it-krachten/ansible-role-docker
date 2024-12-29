[![CI](https://github.com/de-it-krachten/ansible-role-docker/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-docker/actions?query=workflow%3ACI)


# ansible-role-docker

Installs & configures Docker CE   



## Dependencies

#### Roles
None

#### Collections
- ansible.posix
- community.docker
- community.general

## Platforms

Supported platforms

- Red Hat Enterprise Linux 8<sup>1</sup>
- Red Hat Enterprise Linux 9<sup>1</sup>
- CentOS 7<sup>1</sup>
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
# -----------------------------------------
# Docker package repository
# -----------------------------------------

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
    repo_url: https://download.docker.com/linux/debian
    gpg_key: https://download.docker.com/linux/debian/gpg
  Ubuntu:
    repo_url: https://download.docker.com/linux/ubuntu
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


# -----------------------------------------
# Docker OS settings
# -----------------------------------------

# Should cgroups v2 be enabled (Fedora only)
docker_cgroups_v2: false


# -----------------------------------------
# Docker storage
# -----------------------------------------

docker_lvm: false

# -----------------------------------------
# Docker networking
# -----------------------------------------

# Enable networking from container -> outsite-world
docker_networking_outbound: false

## Proxy configuration (for Docker itself)
# docker_http_proxy: http://192.168.1.1:8080
# docker_https_proxy: http://192.168.1.1:8080
# docker_no_proxy: "localhost, 127.0.0.*"

# Activate this boolean to force container to use proxy
docker_proxy_containers: false
docker_proxy_container_settings:
  proxies:
    "http-proxy": "{{ docker_http_proxy | default('') }}"
    "https-proxy": "{{ docker_https_proxy | default('') }}"
    "no-proxy": "{{ docker_no_proxy | default('') }}"
docker_proxy_container_settings_clear:
  proxies: {}

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

# Debian requires diferent naming from Ansible
docker_arch_mapping:
  armv6l: "armhf"
  armv7l: "armhf"
  aarch64: "arm64"
  x86_64: "amd64"
  i386: "i386"


# -------------------------------------------------
# Apt specific settings
# -------------------------------------------------

# Lookup the value we need for Debian/apt
docker_apt_arch: "{{ docker_arch_mapping[ansible_architecture] }}"

# Docker release channel
docker_apt_release_channel: stable

# APT key error ignore?
docker_apt_ignore_key_error: true

# Docker
docker_apt_repo_url: https://download.docker.com/linux

# APT GPG url
docker_apt_gpg_key: "{{ docker_apt_repo_url }}/{{ ansible_distribution | lower }}/gpg"

# Docker APT repostory
docker_apt_repository: >-
  deb [arch={{ docker_apt_arch }}] {{ docker[ansible_distribution]['repo_url'] }}
  {{ ansible_distribution_release }} {{ docker_apt_release_channel }}
</pre></code>

### defaults/family-Debian.yml
<pre><code>
# OS release
# docker_os_release: "{{ ansible_distribution_major_version }}"

# Docker CE packages
docker_packages:
  - docker-ce

# List of required packages before installing Docker
docker_packages_prereqs:
  - apt-transport-https
  - ca-certificates
  - curl
  - gnupg
  - lsb-release
</pre></code>

### defaults/family-RedHat.yml
<pre><code>
# OS release
# docker_os_release: "{{ ansible_distribution_major_version }}"

# Docker CE packages
docker_packages:
  - docker-ce

# List of required packages before installing Docker
docker_packages_prereqs:
  - yum-utils
  - device-mapper-persistent-data
  - lvm2
  # - gcc
  # - glibc-devel
  # - python
  # - python-libs
  # - python-devel
  # - python-pip
</pre></code>

### defaults/family-Suse.yml
<pre><code>
# OS release
# docker_os_release: "{{ ansible_distribution_major_version }}"

# Docker CE packages
docker_packages:
  - docker

# List of required packages befoer installing Docker
docker_packages_prereqs: []
</pre></code>




## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'docker'
  hosts: all
  become: 'yes'
  vars:
    docker_lvm: false
    docker_vg: dockervg
    docker_pv: /dev/sdb
    docker_root: /export/docker
    docker_lvm_setup: '{''vg'': [{''name'': ''{{ docker_vg }}'', ''pv'': ''{{ docker_pv
      }}''}], ''lv'': [{''name'': ''lv_docker'', ''vg'': ''{{ docker_vg }}'', ''size'':
      ''10G'', ''mp'': ''/var/lib/docker'', ''fstype'': ''xfs''}, {''name'': ''lv_docker_data'',
      ''vg'': ''{{ docker_vg }}'', ''size'': ''10G'', ''mp'': ''{{ docker_root }}'',
      ''fstype'': ''xfs''}]}'
  tasks:
    - name: Include role 'docker'
      ansible.builtin.include_role:
        name: docker
</pre></code>
