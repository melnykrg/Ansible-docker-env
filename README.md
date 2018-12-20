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


