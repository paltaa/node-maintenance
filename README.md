# node-maintentenance

## Description

MySQL node maintenance task runner Ansible role

## Usage

All scripts in ./roles/maintenance/files/scripts will be executed in each of the nodes.

Set nodes in inventory file, mount keys in docker container if necesary or set path in inventory file

## Deploy

Deploy with ansible script deploy.yml will setup docker container as a cronjob for each hour

Deploy with Kubernetes Cronjob will setup a cronjob each hour with no paralellism and wont trigger a new job if the last ona has not finished

### Requirements


Option 1:

- vagrant
- virtualBox
- Ansible
- sshpass (sshs for MacOs)
  
Option 2:

- Docker
- Docker-compose

## Development

Option 1: playbook runs in host and connects to vm provisioned by vagrant

Setup VM

```bash
vagrant up
```

Run playbook

```bash
ansible-playbook main.yaml -i inventory -l development -b
```



Option 1: playbooks run in docker

Run command will setup 2 servers with ssh service running on port 2222

```bash
docker-compose up
```


