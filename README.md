# DevOpsGitlab
Concentrating Devops knowledge with Gitlab Ci / CD

## Start
Change to `compose` folder and run:
```
docker-compose up -d
```
List Docker containers
```
docker ps --format "table {{.ID}}\t{{.Status}}\t{{.Names}}"
```
Connect to the container running the Gitlab runner
```
docker exec -it <container ID> /bin/bash
```
## Add Runner
### Register the runner 
As per Admin Area / Overview / Runners / Show Runner installation instructions. Token as per run.
```
sudo gitlab-runner register --url http://172.30.0.5/ --registration-token fvxNvA9N2WSkHn6bv4ys
```
### Configure runner network
In `/etc/gitlab-runner/config.toml` add the Docker Compose created network:
```
[runners.docker]
   network mode= "gitlab"
```
### Restart runner container
```
docker restart <container ID>
```

### Resources
```
https://serverfault.com/a/1020417
```

