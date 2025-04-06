# Jenkins Docker outside of Docker Setup

This setup makes building container happens outside jenkins container (host machine) for one machine setup.

## Clone Project
```bash
git clone raditsoic/jenkins-setup
```

## Match Host Docker GID with Jenkins Dockerfile

Get Docker GID on Host Machine then change the GID in the Dockerfile
```bash
getent group docker | cut -d: -f3
```

## Build Jenkins Image
```bash
docker build -t jenkins-server .
```

## Run Jenkins Server
```bash
docker run -d -p 8080:8080 -p 50000:50000 \
  -v jenkins_home:/var/jenkins_home \
  -v /var/run/docker.sock:/var/run/docker.sock \
  --name jenkins-blueocean jenkins-with-docker:latest
```
