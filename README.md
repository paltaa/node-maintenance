# node-maintentenance

## Description

MySQL node maintenance task runner Ansible role

## Instructions

Setting up development and production environment for node-maintenance task

### Data Dog integration

1. Set api key

```bash
export DATADOG_API_KEY=<your-api-key>
echo "api_key: ${DATADOG_API_KEY}" >> ./callback_plugins/datadog_callback.yml
```

2. Install requirements

```bash
pip install -r ./callback_plugins/requirements.txt
```

### Set variables and inventory

Set variables in .`/variables.yaml`

All scripts in ./roles/maintenance/files/scripts will be executed in each of the nodes.

Set nodes in `inventory` files and credentials for ssh


## Deploy

Copy crontab from `deploy/crontab` example and add to your server crontab after installing dependencies and cloning repository.


###┬áKubernetes Cronjob

will setup a cronjob each hour with no paralellism and wont trigger a new job if the last one has not finished

1. Build and push the image to a container registry

2. Set variables:
    activeDeadlineSeconds: 3600 # Maximum amount of time in seconds to the job
    image: container-image-url:tag # Container registry url and tag

### Deploy with Ansible playbook

Did not have time to write this one:

Deploy with ansible script `deploy.yml` will setup ansible as a cronjob for each hour


## Development

### Requirements

- vagrant
- virtualBox
- Ansible
- sshpass (sshs for MacOs)

### Instructions

Set variables in .`/variables.yaml`

Playbook runs in host and connects to vm provisioned by vagrant

Setup VM

```bash
vagrant up
```

Run playbook

```bash
ansible-playbook main.yaml -i inventory -l development -b
```

In another terminal, connect to VM with ssh

```bash
vagrant ssh
```

