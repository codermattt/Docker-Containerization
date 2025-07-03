# Containerize multi-tier application: 
  # Notes
    - changed names of files so it is easier to identify

  # Scenario:
    - multi-tier application stack
    - app running on vms/cloud/physical OS
    - Regular deployment for any changes to app
  
  # Notes:
    - source code -> https://github.com/hkhcoder/vprofile-project.git
    - installed docker engine on an ubuntu OS virtual-machine
    - created 3 Dockerfiles, configured according to the application needs
    - pulled the default Memcached and RabbitMQ images off Dockerhub
    
  # Brief steps to setup stack services:
    - Find Base Image from Dockerhub
    - Write Dockerfile to customize images
    - Create Dockerhub repos to push images to
    - Write docker-compose.yml file to run multi-containers
    - Test and host images on Dockerhub
