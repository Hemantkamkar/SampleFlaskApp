# SampleFlaskApp
pythonapp

# Docker-compose Install

- Download Docker Compose `sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose`

- Makde Docker Compose Executable - `sudo chmod +x /usr/local/bin/docker-compose`

- Check Docker Compose Version - `docker-compose --version`

# Create docker compose yaml file
- vi docker-compose.yml
- paste docker-compose.yml code

# Execute commands
- docker-compose up -d
- docker volume ls
- docker ps
  
# Run jenkins server and get the password commands
- docker run -p 8080:8080 -p 50000:50000 -d --name jenkins --restart=on-failure -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts-jdk21
- docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword




