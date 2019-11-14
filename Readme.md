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

Customization
------------------------
If you need to change any behaviours simply fork the relevant repository/s (frontend, web-service, setup-tool, background-worker).
In the directory of the Nebula Docker repository create a new file `docker-compose.override.yaml` with the following contents;
```yaml
version: '3.7'
services:
# To modify the frontend, fork the repository below, make changes, and update the url
  frontend:
    build:
      context: https://github.com/nebula-analytics/nebula.git
      
# To modify the web service, fork the repository below, make changes, and update the url
  web-service:
    build:
      context: https://github.com/nebula-analytics/nebula-webservice.git
      
# To modify the setup tool, fork the repository below, make changes, and update the url
  setup-tool:
    build:
      context: https://github.com/nebula-analytics/nebula-automated-setup.git
 
# To modify the background worker, fork the repository below, make changes, and update ALL the urls below
  node-1:
    build:
      context: https://github.com/nebula-analytics/nebula-background-worker.git
  node-2:
    build:
      context: https://github.com/nebula-analytics/nebula-background-worker.git
  node-schedule:
    build:
      context: https://github.com/nebula-analytics/nebula-background-worker.git
```
For example, to change the frontend to the RMIT branded version create the following docker-compose.override.yaml file.
```docker-compose.yaml
version: '3.7'
services:
  frontend:
    build:
      # Notice how you can specify a specific branch as well.
      context: https://github.com/nebula-analytics/nebula.git#deploy/rmit-uat
```
All you need to do now to deploy your changes is run the command
```
docker-compose up -d --build
```
