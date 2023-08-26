
Download, install and run:

Docker: (https://www.jenkins.io/doc/book/installing/docker/)

	. docker pull jenkins/jenkins:lts-jdk11
	. docker network create jenkins
	. docker run \
  --name jenkins-docker \
  --rm \
  --detach \
  --privileged \
  --network jenkins \
  --network-alias docker \
  --env DOCKER_TLS_CERTDIR=/certs \
  --volume jenkins-docker-certs:/certs/client \
  --volume jenkins-data:/var/jenkins_home \
  --publish 2376:2376 \
  docker:dind \
  --storage-driver overlay2
  		
  	. create Dockerfile	
  	. docker build -t myjenkins-blueocean:2.414.1-1 .
  	. docker run \
  --name jenkins-blueocean \
  --restart=on-failure \
  --detach \
  --network jenkins \
  --env DOCKER_HOST=tcp://docker:2376 \
  --env DOCKER_CERT_PATH=/certs/client \
  --env DOCKER_TLS_VERIFY=1 \
  --publish 8080:8080 \
  --publish 50000:50000 \
  --volume jenkins-data:/var/jenkins_home \
  --volume jenkins-docker-certs:/certs/client:ro \
  myjenkins-blueocean:2.414.1-1
  
  	. docker logs <myjenkins-blueocean container name>
  	(to check out the username and password)
  	
  	. paste -> http://localhost:8080
  	. paste password from logs
  	. Install recomended plugins
  	. create admin user -> dejvis, password

