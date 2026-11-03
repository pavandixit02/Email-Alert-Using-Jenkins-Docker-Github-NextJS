# Automated Email Alert System Using Jenkins, Docker, GitHub Webhooks & NestJS

<p align="center">
  <a href="http://nestjs.com/" target="blank">
    <img src="https://nestjs.com/img/logo-small.svg" width="120" alt="Nest Logo" />
  </a>
</p>

[circleci-image]: https://img.shields.io/circleci/build/github/nestjs/nest/master?token=abc123def456
[circleci-url]: https://circleci.com/gh/nestjs/nest

<p align="center">
  A progressive <a href="http://nodejs.org" target="_blank">Node.js</a> framework for building efficient and scalable server-side applications.
</p>

<p align="center">
  <a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/v/@nestjs/core.svg" alt="NPM Version" /></a>
  <a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/l/@nestjs/core.svg" alt="Package License" /></a>
  <a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/dm/@nestjs/common.svg" alt="NPM Downloads" /></a>
  <a href="https://circleci.com/gh/nestjs/nest" target="_blank"><img src="https://img.shields.io/circleci/build/github/nestjs/nest/master" alt="CircleCI" /></a>
  <a href="https://discord.gg/G7Qnnhy" target="_blank"><img src="https://img.shields.io/badge/discord-online-brightgreen.svg" alt="Discord"/></a>
  <a href="https://opencollective.com/nest#backer" target="_blank"><img src="https://opencollective.com/nest/backers/badge.svg" alt="Backers on Open Collective" /></a>
  <a href="https://opencollective.com/nest#sponsor" target="_blank"><img src="https://opencollective.com/nest/sponsors/badge.svg" alt="Sponsors on Open Collective" /></a>
  <a href="https://paypal.me/kamilmysliwiec" target="_blank"><img src="https://img.shields.io/badge/Donate-PayPal-ff3f59.svg" alt="Donate us"/></a>
  <a href="https://opencollective.com/nest#sponsor" target="_blank"><img src="https://img.shields.io/badge/Support%20us-Open%20Collective-41B883.svg" alt="Support us"></a>
  <a href="https://twitter.com/nestframework" target="_blank"><img src="https://img.shields.io/twitter/follow/nestframework.svg?style=social&label=Follow" alt="Follow us on Twitter"></a>
</p>

---

## 📌 Project Overview

The **Automated Email Alert System** is a DevOps-focused CI/CD automation project that integrates GitHub Webhooks, Jenkins, Docker, and NestJS to automate application build, deployment, and email notification processes.

Whenever a developer pushes new code to the GitHub repository, GitHub Webhooks trigger the Jenkins pipeline. Jenkins automatically retrieves the latest source code, builds a Docker image, manages the previous application container, and deploys the updated application.

After successful deployment, Jenkins sends an email notification to the configured recipient.

This project demonstrates how multiple DevOps tools work together to create an automated application delivery workflow with minimal manual intervention.

## 🎯 Project Objectives

- Automate application deployment using Jenkins.
- Integrate GitHub with Jenkins through Webhooks.
- Build and package applications using Docker.
- Automate Docker container lifecycle management.
- Send email notifications after successful deployment.
- Understand practical CI/CD pipeline implementation.
- Reduce manual deployment activities.
- Gain hands-on experience with DevOps tools and workflows.

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| NestJS | Backend application framework |
| Node.js | JavaScript runtime |
| TypeScript | Application development |
| Git | Version control |
| GitHub | Source code repository |
| GitHub Webhooks | Automated pipeline triggering |
| Jenkins | CI/CD automation |
| Jenkins Pipeline | Deployment workflow |
| Docker | Application containerization |
| Docker Image | Application packaging |
| Email Extension Plugin | Email notifications |
| Ubuntu Linux | Development and deployment environment |

## 🏗️ Project Architecture

The project follows an automated CI/CD architecture where GitHub acts as the source code repository and Jenkins manages the application build and deployment process.

### CI/CD Workflow

```text
                  Developer
                      |
                      |
                   Git Push
                      |
                      v
              GitHub Repository
                      |
                      |
                GitHub Webhook
                      |
                      v
                   Jenkins
                      |
                      v
              Clone Repository
                      |
                      v
              Build Docker Image
                      |
                      v
           Stop Previous Container
                      |
                      v
          Remove Previous Container
                      |
                      v
           Run New Docker Container
                      |
                      v
           Send Email Notification
                      |
                      v
              Deployment Complete
```

## ⚙️ How the Project Works

### 1. GitHub Integration

The application source code is maintained in a GitHub repository.

Whenever a developer pushes new changes to the configured branch, GitHub Webhooks notify Jenkins and trigger the CI/CD pipeline.

### 2. Jenkins Pipeline Execution

Jenkins automatically retrieves the latest source code and executes the stages defined in the Jenkinsfile.

The pipeline manages repository checkout, Docker image creation, container replacement, application deployment, and email notification.

### 3. Docker Image Creation

Jenkins uses the project's Dockerfile to build a Docker image.

The image contains the application source code, required dependencies, and Node.js runtime environment.

### 4. Container Management

Before deploying the updated application, Jenkins attempts to stop and remove the previous application container.

It then creates a new container using the newly built Docker image.

### 5. Email Notification

After successful deployment, Jenkins sends an email notification to the configured recipient.

The notification confirms that the deployment process has completed successfully.

## 🔄 Jenkins Pipeline Stages

The Jenkinsfile defines the following stages:

| Pipeline Stage | Description |
|---|---|
| Declarative Checkout SCM | Retrieves the Jenkinsfile and repository source code |
| Clone Repo | Checks out the latest application code |
| Build Docker Image | Builds a Docker image using the Dockerfile |
| Stop & Remove Previous Container | Stops and removes the previous application container if present |
| Docker Container Run | Starts the updated application container |
| Send Email Notification | Sends deployment confirmation through email |

## 📁 Project Directory Structure

```text
Email-Alert-Using-Jenkins-Docker-Github-NextJS/
│
├── .dockerignore
├── .gitattributes
├── .gitignore
├── .oxlintrc.json
├── .prettierrc
├── 1.txt
├── AGENTS.md
│
├── Dockerfile
├── Jenkinsfile
├── README.md
│
├── Output Imges/
│   ├── Pipeline-Steps.png
│   ├── Polling-Log.png
│   ├── Status.png
│   └── start-end-process.png
│
├── nest-cli.json
├── package.json
├── package-lock.json
│
├── src/
│   ├── app.controller.spec.ts
│   ├── app.controller.ts
│   ├── app.module.ts
│   ├── app.service.ts
│   └── main.ts
│
├── test/
│   └── app.e2e-spec.ts
│
├── tsconfig.build.json
├── tsconfig.json
├── vitest.config.e2e.ts
└── vitest.config.ts
```

## 🐳 Docker Configuration

Docker is used to package the NestJS application into a portable container image.

The project uses Node.js 24 Alpine as the Docker base image.

### Docker Responsibilities

- Provides a consistent Node.js runtime.
- Installs application dependencies.
- Copies application source code.
- Compiles the NestJS application.
- Exposes the application port.
- Starts the compiled application.

### Container Configuration

| Configuration | Value |
|---|---|
| Base Image | Node.js 24 Alpine |
| Working Directory | `/app` |
| Application Port | 3300 |
| Docker Image Name | `nesths-image` |
| Container Name | `nestjs-app` |
| Host Port | Configured in Jenkinsfile |

## 📧 Email Notification System

Email notifications are integrated into the Jenkins pipeline using the Email Extension Plugin.

After successful application deployment, Jenkins sends an email containing deployment information.

### Notification Workflow

1. Jenkins completes the Docker image build.
2. Jenkins deploys the updated application container.
3. The email notification stage executes.
4. The configured recipient receives a deployment confirmation.

Email notifications help developers monitor deployment activities without manually checking the Jenkins dashboard after every successful build.

**Note:** The current pipeline sends its email notification after successful deployment. Failure notifications can be implemented separately using Jenkins post-build actions.

## 📸 Project Screenshots

The following screenshots demonstrate the Jenkins CI/CD pipeline, polling activity, build status, and application deployment workflow.

### 1. Jenkins Pipeline Steps

Displays the different stages of the automated Jenkins pipeline, including repository checkout, Docker image building, container deployment, and email notification.

![Jenkins Pipeline Steps](Output%20Imges/Pipeline-Steps.png)

### 2. GitHub Polling Logs

Shows Jenkins polling activity and related execution logs used to monitor repository changes and pipeline triggering.

![Polling Log](Output%20Imges/Polling-Log.png)

### 3. Jenkins Build Status

Displays the Jenkins job execution status and pipeline result.

![Jenkins Build Status](Output%20Imges/Status.png)

### 4. Application Start and End Process

Demonstrates the application deployment workflow and its start and end processes.

![Application Start and End Process](Output%20Imges/start-end-process.png)

## 🔐 Configuration and Security

For a secure deployment setup:

- Configure SMTP details in Jenkins instead of hardcoding credentials.
- Store sensitive information in Jenkins Credentials.
- Avoid committing passwords, API keys, and private tokens.
- Restrict access to the Jenkins dashboard.
- Use trusted Docker images.
- Keep application dependencies updated.
- Restrict access to the Docker socket.
- Protect GitHub webhook configuration and deployment endpoints.

## 🚀 Application Deployment

Application deployment is automated through the Jenkins pipeline.

The deployment workflow includes:

1. Pushing application changes to GitHub.
2. Triggering Jenkins through the configured GitHub Webhook.
3. Retrieving the latest application source code.
4. Building the updated Docker image.
5. Stopping and removing the previous application container.
6. Starting the new application container.
7. Sending an email notification after successful deployment.

The NestJS application listens on port `3300` by default. The externally mapped host port is configured in the Jenkinsfile.

## 🧪 Testing and Validation

The project includes testing support through Vitest and NestJS testing utilities.

The available project scripts support:

- Unit testing.
- End-to-end testing.
- Test coverage.
- Application build validation.

These tests help validate application functionality and maintain code quality.

## 📚 Key DevOps Concepts Demonstrated

This project provides practical experience with:

- Continuous Integration (CI).
- Continuous Deployment (CD).
- GitHub Webhook Integration.
- Jenkins Declarative Pipeline.
- Docker Image Building.
- Docker Container Lifecycle Management.
- Automated Application Deployment.
- Email-Based Deployment Notifications.
- Linux-Based CI/CD Environment.
- Application Containerization.
- Build and Deployment Automation.

## 🔮 Future Improvements

Potential improvements for extending this project include:

- Add automated unit and integration testing stages.
- Implement email alerts for failed deployments.
- Add Docker image tagging and version management.
- Push Docker images to Docker Hub.
- Add deployment rollback functionality.
- Integrate Prometheus and Grafana monitoring.
- Add automated security and vulnerability scanning.
- Deploy the application to a cloud platform.
- Introduce separate development, staging, and production environments.

## 📖 Learning Outcomes

Through this project, the following practical skills can be developed:

- Understanding how GitHub Webhooks trigger Jenkins pipelines.
- Creating and managing Jenkins CI/CD pipelines.
- Building Docker images for Node.js applications.
- Managing application containers during deployment.
- Integrating email notifications into automated workflows.
- Troubleshooting Docker and Jenkins integration issues.
- Understanding the complete source-code-to-deployment workflow.

## 🔗 Project Repository

**GitHub Repository:**

[Email Alert Using Jenkins, Docker, GitHub Webhooks & NestJS](https://github.com/pavandixit02/Email-Alert-Using-Jenkins-Docker-Github-NextJS)

## 📚 Resources

- [NestJS Documentation](https://docs.nestjs.com/)
- [Node.js Documentation](https://nodejs.org/docs/)
- [Docker Documentation](https://docs.docker.com/)
- [Jenkins Documentation](https://www.jenkins.io/doc/)
- [GitHub Webhooks Documentation](https://docs.github.com/en/webhooks)
- [Git Documentation](https://git-scm.com/doc)

## 🤝 Contributing

Contributions, suggestions, and improvements are welcome.

If you find an issue or have an idea to improve this project, feel free to open an issue or submit a pull request.

## 👨‍💻 Author

**Pavan Kumar Dixit**

Cloud & DevOps Enthusiast

- GitHub: [@pavandixit02](https://github.com/pavandixit02)
- LinkedIn: [Connect on LinkedIn](https://www.linkedin.com/in/pavan-dixit-677558291)
- X: [@pavandixit775](https://x.com/pavandixit775)

---

<p align="center">
  Built with ❤️ using NestJS, Docker, Jenkins, and GitHub Webhooks.
</p>
