# Overview of Dockerfiles configured
  
  # Client Dockerfile:
    - built artifact with node
    - copy artifact into default nginx html path
    - copy nginx.conf file into default configuration path of nginx
      - specifies which files to present to user, from the artifact
  
  # NodeApi Dockerfile:
    - build artifact with node
    - copy artifact to app directory
    - then CMD starts the container
  
  # JavaApi Dockerfile:
    - install maven on WORKDIR, copy soure code on WORKDIR
    - mvn install to build artifact
    - move file to WORKDIR to run
  
  # Nginx:
    - default.conf to be loaded as volume to container
    - apigateway/default.conf file has configurations for routing to different container microservices
  
  # Docker-compose file
    - the api, webapi and client containers need other containers to be running before it starts
    - nginx container has default.conf volume mapped to default.conf file of container
    - set database name of emongo container to "epoc", as required by the nodeapi/config/keys.js file, for nodeapi container to connect to a database named "epoc"
    - the nginx, emongo and emartdb containers used their default images off Dockerhub.

# Build and Run:
  - used an ubuntu ec2 instance with t3-medium instance type (faster, more RAM)
  - increased volume size to 15GB,  default 8GB is too small
  - added provisioning script to install Docker engine + docker-compose + added ubuntu user into docker group
  - logged in and pulled source code from https://github.com/devopshydclub/emartapp.git
  - added Dockerfiles and Docker-compose files into working directory of project and Source code
  - built and ran containers off docker-compose file

