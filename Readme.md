Project Nebula (Docker Deployment)
==================================
Prerequisites
------------------------
1. Install Docker and Docker-compose (https://docs.docker.com/compose/install/)
2. You will need to obtain a token for google analytics, using https://github.com/nebula-analytics/nebula-ganalytics-poc.
3. You will need to create a config.yaml.secret with additional configuration information (see nebula-background-worker for more info)
4. We recommend changing the default mongodb password in the docker-compose file

Installation
------------------------
#### 1.
Clone this repository using the following command;
```
git clone https://github.com/nebula-analytics/nebula-docker --recurse-submodules
```

#### 2.
Spin up the application by running the following command from the nebula-docker directory;
```
docker-compose up -d --build
```

Updating
------------------------
To update you simply need to pull changes from github with the following command;
```
git pull --recurse-submodules
```

Once the changes have been pulled, you can tell docker to replace the updated nodes with the command;
```
docker-compose up -d --build
```