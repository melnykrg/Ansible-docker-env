# Udemy Mastering Ansible Course

I recently purchased the [Udemy Mastering Ansible Course](https://www.udemy.com/mastering-ansible/learn/v4/). The course instructor mentions that he is using a Docker environment for the exercises, however I wasn't able to find a copy of this configuration to use. While there is a [Vagrant](https://www.vagrantup.com) file provided, I'd prefer not to install [VMware Fusion](https://www.vmware.com/products/fusion.html) or [VirtualBox](https://www.virtualbox.org) if I can avoid it and already have [Docker for macOS](https://www.docker.com/docker-mac) installed.

## Course Topology
The topology of the course, provided by the instructor, is included in the [Topology.pdf](Topology.pdf) file within this repository.

## Requirements
Docker and docker-compose, python, pip


    `docker-compose up --build -d`


    `docker exec -it "control_container_id" bash`


    `ansible all -m ping`


## Commands

### Startup the Environment
`docker-compose up --build -d`

### Connect to the Environment
`docker exec -it udemy-mastering-ansible_control_1 bash`

### Shutdown The Environment
`docker-compose down --remove-orphan`

### Update to latest project version
`git pull`


### Get list of docker IPs
`docker inspect -f '{{.Name}} - {{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' $(docker ps -q) `


