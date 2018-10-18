# Ansible Role: Docker for china

[![Build Status](https://travis-ci.org/pytool/ansible-role-docker.svg?branch=master)](https://travis-ci.org/pytool/ansible-role-docker)

An Ansible Role that installs [Docker](https://www.docker.com) on Linux.

## Example Playbook

```yaml
- hosts: localhost
  become: yes
  roles:
    - pytool.docker
  vars:
    - docker_compose_install: true
    # - docker_machine_install: true
```

## 1.安装docker
ansible-playbook -vv tests/docker.yml

## 2.卸载docker
ansible-playbook --tags 'clean' -vv tests/docker.yml

## 3. Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):
```yml
docker_version: "18.06.1-ce"
docker_checksum_sha256: "83be159cf0657df9e1a1a4a127d181725a982714a983b2bdcc0621244df93687  docker-18.06.1-ce.tgz"
docker_download_url: "https://mirrors.aliyun.com/docker-ce/linux/static/stable/x86_64/docker-{{docker_version}}.tgz"
##### docker_download_url: "https://download.docker.com/linux/static/stable/x86_64/docker-{{docker_version}}.tgz"

docker_compose_install: false
docker_compose_version: "1.21.2"
docker_compose_checksum_sha256: "8a11713e11ed73abcb3feb88cd8b5674b3320ba33b22b2ba37915b4ecffdf042  docker-compose-Linux-x86_64"
docker_compose_url: "https://mirrors.aliyun.com/docker-toolbox/linux/compose/{{docker_compose_version}}/docker-compose-Linux-x86_64"
##### docker_compose_url: "https://github.com/docker/compose/releases/download/{{ docker_compose_version }}/docker-compose-Linux-x86_64"

docker_machine_install: false
docker_machine_version: "0.15.0"
docker_machine_checksum_sha256: "44c5c62db13b6eb6a9d3e276c1181401c78327ff6303570936ba2cf5d137b7b5  docker-machine-Linux-x86_64"
docker_machine_url: "https://mirrors.aliyun.com/docker-toolbox/linux/machine/{{docker_machine_version}}/docker-machine-Linux-x86_64"

#### 默认二进制文件目录 main.yml 所在的路径
docker_download_dir: "./"
docker_bin_dir: "/usr/local/bin"
#### docker镜像和容器存储目录 --graph=/var/lib/docker
docker_data_dir: "/data/lib/docker"

#### a list of users who will be added to the docker group.
docker_users: [ubuntu,]
docker_user: "docker"
docker_group: "docker"
docker_gid: 999
docker_uid: 999
#### /etc/docker/daemon.json
#### 1.国内镜像加速
reg_mirror_1: "https://registry.docker-cn.com"
reg_mirror_2: "https://docker.mirrors.ustc.edu.cn"
reg_mirror_3: "http://hub-mirror.c.163.com"

#### 2.docker  日志相关
log_driver: "json-file"
log_level: "warn"
log_max_size: "10m"
log_max_file: 3
```


## License

MIT / BSD

## Author Information

This role was created in 2018 by [pytool](https://blog.pytool.com/)