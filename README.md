# comp90024-ansible-scaffolding
A simple playbook to automatically create instance and deploy software instances on the remote server. In the Assignment 2, a team is expected to:
1. Create a MRC instance and obtain the IP address of this instance
2. Deploy everything needed onto this remote server

## Playbook Structure
- `ansible.cfg`: Ansible configuration file to add some configurations into the playbook. Can leave blank
- `common.yml`: Common tasks that are involved by all other tasks (e.g. create docker network since all the container should be included in this network)
- `couchdb.yml`: Automation process for 
  - Stoping, removing CouchDB container
  - Removing docker image (if possible)
  - Re-pull the image from docker hub (if possible)
  - Recreate and start the CouchDB container
- `django.yml`: Automation process for
  - Stoping, removing Django container
  - Removing docker image
  - Re-build the docker image by running `Dockerfile`
  - Recreate and start the Django container
- `hosts`: Define server address. Can be described as key-value pairs
- `instance.yml`: Automation process for creating a MRC instance
- `main.yml`: Main process gathering other tasks. Tasks are executed sequentially.
- `pre_install.yml`: Can leave black if nothing needs to be installed on the server prior to other tasks
- `react.yml`: Automation process for 
  - Stoping, removing React container
  - Removing all necessary docker images (react, nginx, node)
  - Re-build the docker image by running `Dockerfile`
  - Recreate and start the React container
- `run.sh`: Entrance for this playbook.
- `vars.yml`: Variables that are used by other tasks.

## Execute the Playbook
Before execution, replace anything necessary with your own things (e.g. project_name, repo_path, etc) and run:
```bash
./run.sh
```
Note that your **OpenRC.sh** file should be in the same directory as your playbook **main.yml** file.

## Reference Documentations
1. https://docs.ansible.com/ansible/latest/collections/openstack/cloud/index.html
2. https://docs.ansible.com/ansible/latest/collections/community/docker/index.html
