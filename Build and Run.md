# Application services/stack + version of Docker image used:
  - MySQL -> 8.0.33
  - Memcache -> latest
  - RabbitMQ -> latest
  - JDK -> jdk21
  - Maven -> 3.9.9
  - Tomcat -> 10
  - Nginx -> 1.27
# Summaries of Dockerfiles used
  # App Dockerfile:
    - built artifact with Maven
    - then moved from Maven build image to  deploy on Tomcat image
    - this reduces the size of the image that hosts the app (tomcat)

  # DB Dockerfile:
    - set database name and Root password
    - copied database configuration file to the default MySQL database configuration path, to initialize to the database

  # web Dockerfile
    - removed the default nginx config file
    - mounted a configuration file into the default nginx file
    - the config file routes a URL request to the tomcat container named "vproapp"
    
  # Docker-compose file:
    - set names for the services/containers and the paths for the Dockerfiles(for the services with Dockerfiles)
    - set host port to container port mapping + set environment variables for RabbitMQ and MySQL (vprodb)
    - containers will use image in specified Dockerhub account and repo, after it is pushed to Dockerhub
    - before it is pushed, it will use the Dockerfile path specified.
    - After verifying the Dockerfiles' configuration worked for the application, it was pushed to Dockerhub

# BUILD and RUN
  - built images inside an ubuntu VM
  - moved to the working directory with the Vagrantfile, Docker-files and Docker-compose file present
  - started and ran containers, then confirmed application worked with ip address of virtual machine on brower
  - I connected to my Dockerhub account (https://hub.docker.com/repositories/devopper000) using the generated one-time pin on the terminal
  - I pushed the images

