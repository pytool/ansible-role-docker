# Ansible Role: Docker

[![Build Status](https://travis-ci.org/pytool/ansible-role-docker.svg?branch=master)](https://travis-ci.org/pytool/ansible-role-docker)

An Ansible Role that installs [Docker](https://www.docker.com) on Linux.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):
base_dir: "."
bin_dir: "/usr/local/bin/"
docker_install_compose: false

# a list of users who will be added to the docker group.
docker_users: []

# /etc/docker/daemon.json
# 1.国内镜像加速
reg_mirror_1: "https://registry.docker-cn.com"
reg_mirror_2: "https://docker.mirrors.ustc.edu.cn"

# 2.docker  日志相关
log_driver: "json-file"
log_level: "warn"
log_max_size: "10m"
log_max_file: 3

# 3.docker容器存储目录
storage_dir: "/var/lib/docker"


(Used only for RedHat/CentOS.) You can enable the Edge or Test repo by setting the respective vars to `1`.

    docker_users:
      - user1
      - user2

A list of system users to be added to the `docker` group (so they can use Docker on the server).

## Use with Ansible (and `docker` Python library)

Many users of this role wish to also use Ansible to then _build_ Docker images and manage Docker containers on the server where Docker is installed. In this case, you can easily add in the `docker` Python library using the `pytool.pip` role:

```yaml
- hosts: all
  roles:
    - pytool.docker
```

## Dependencies

None.

## Example Playbook

```yaml
- hosts: all
  roles:
    - pytool.docker
```

## License

MIT / BSD

## Author Information

This role was created in 2017 by [Jeff Geerling](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).
