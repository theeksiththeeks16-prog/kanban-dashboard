# Docker CI/CD Pipeline with Jenkins on AWS EC2

## Project Overview

This project demonstrates an automated CI/CD pipeline to build, push, and deploy a web application using GitHub, Jenkins, Docker, Docker Hub, and AWS EC2.

Whenever code is pushed to GitHub, the configured webhook triggers Jenkins to automatically execute the pipeline, build a Docker image, push it to Docker Hub, deploy it to the EC2 instance, and validate the deployment.

## Architecture

**GitHub → GitHub Webhook → Jenkins → Docker Build → Docker Hub → AWS EC2 → Container Deployment → Validation**

## Technologies Used

- **GitHub** – Source code management
- **GitHub Webhooks** – Automatic pipeline triggering on code pushes
- **Jenkins** – CI/CD automation
- **Docker** – Containerization
- **Docker Hub** – Docker image registry
- **AWS EC2** – Cloud deployment server
- **Linux (Amazon Linux)** – Server operating system

## CI/CD Pipeline Stages

1. **Checkout** – Fetch source code from the GitHub repository.
2. **Build Docker Image** – Build the application Docker image.
3. **Push to Docker Hub** – Upload the image to Docker Hub.
4. **Deploy** – Deploy the latest application image to the EC2 server.
5. **Verify Deployment** – Verify that the deployed application is running.

## Automated Workflow

1. Developer pushes code to GitHub.
2. GitHub webhook sends a push event to Jenkins.
3. Jenkins automatically starts the pipeline.
4. Jenkins checks out the latest source code.
5. Docker image is built and tagged.
6. The image is pushed to Docker Hub.
7. The application container is deployed on AWS EC2.
8. Deployment is validated.

## Docker Image

**Docker Hub Repository:**  
https://hub.docker.com/r/theeksith/kanban-dashboard

Image naming format:

```text
theeksith/kanban-dashboard:<build-number>
```

The pipeline also updates the `latest` tag.

## Deployment Details

| Configuration | Value |
|---|---|
| Cloud platform | AWS EC2 |
| Application container | kanban-dashboard |
| Docker image | theeksith/kanban-dashboard |
| Container port | 8080 |
| Host port | 8081 |
| Deployment method | Jenkins automated pipeline |
| Container health | Docker health check |

The application is accessible through:

```text
http://<EC2-PUBLIC-IP>:8081
```

## Docker Resource Limits

CPU and memory limits are configured for the deployed application container.

| Resource | Limit |
|---|---|
| Memory | 512 MB |
| Memory + Swap | 768 MB |
| CPU | 0.5 CPU |

These limits help prevent the container from consuming excessive server resources.

## Monitoring and Logs

Docker container logs can be checked using:

```bash
sudo docker logs --tail 20 kanban-dashboard
```

Container resource usage can be monitored using:

```bash
sudo docker stats --no-stream kanban-dashboard
```

Container status can be checked using:

```bash
sudo docker ps
```

## GitHub Webhook

A GitHub webhook is configured to trigger the Jenkins pipeline automatically whenever code is pushed to the repository.

**Webhook event:** Push

**Jenkins trigger:** GitHub hook trigger for GITScm polling

The webhook integration was tested successfully, and Jenkins Build #5 was automatically triggered by a GitHub push and completed successfully.

## Project Validation

The following validations were performed:

- Jenkins pipeline completed successfully.
- Docker image was built successfully.
- Docker image was pushed to Docker Hub.
- Application was deployed on AWS EC2.
- Application was accessible through the configured port.
- Docker container health status was verified.
- GitHub webhook automatically triggered Jenkins.
- CPU and memory limits were applied and verified.
- Docker logs and resource usage were checked.

## Repository

GitHub Repository:

https://github.com/theeksiththeeks16-prog/kanban-dashboard

## Author

**Theeksith S.**

DevOps Project – Automated CI/CD Deployment using Jenkins, Docker, and AWS EC2
