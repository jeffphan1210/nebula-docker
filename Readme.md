Project Nebula (Docker Deployment)
==================================
Prerequisites
------------------------
1. Install Docker and Docker-compose (https://docs.docker.com/compose/install/)

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

#### 3.
Your application is now running, if you navigate to localhost:80 you'll see an empty nebula dashboard.
In order to start populating the dashboard you'll need to access the setup tool and fill in some information.
To access the setup tool;
##### On a remote machine (using ssh access)
```
ssh username@ip_address -L 5000:127.0.0.1:5000 -N
```
Then navigate to http://localhost:5000

##### On a non-headless desktop (locally)
In any web browser, navigate to http://localhost:5000


Follow the steps on the web tool and once completed, nebula should start populating data automatically.

Updating
------------------------
To update you simply need to pull changes from github with the following command;
```
git pull
```

Once the changes have been pulled, you can tell docker to replace the updated nodes with the command;
```
docker-compose up -d --build
```
