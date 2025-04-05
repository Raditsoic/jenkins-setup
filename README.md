# Jenkins Setup

## Clone Project
```bash
git clone raditsoic/jenkins-setup
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
