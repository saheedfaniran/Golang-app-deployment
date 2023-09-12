# Go Application Deployment Pipeline

This project aims to automate the deployment of a Go application into a Kubernetes cluster using Jenkins, Docker, Terraform, and AWS EKS. This README provides an overview of the project and a step-by-step guide to set up and use the deployment pipeline.

## Table of Contents
- [Prerequisites](#prerequisites)
- [Setup](#setup)
- [Jenkins Pipeline](#jenkins-pipeline)
- [Accessing the Application](#accessing-the-application)
- [Maintenance and Troubleshooting](#maintenance-and-troubleshooting)

## Prerequisites

Before setting up the deployment pipeline, ensure you have the following prerequisites:

- An AWS account with permissions to create EC2 instances, EKS clusters, and manage AWS resources.
- An EC2 instance (Ubuntu) with SSH access and inbound traffic allowed on ports 8080 and 22.
- Jenkins installed and running on the EC2 instance.
- Docker installed on the EC2 instance.
- Trivy scanner installed for image vulnerability scanning.
- Terraform installed on the EC2 instance.
- kubectl installed on the EC2 instance.
- AWS CLI installed and configured with proper credentials.
- A GitHub repository containing the Go application code.
- Proper AWS IAM roles and policies set up for EKS access.

## Setup

Follow these steps to set up the project:

1. **Launch an EC2 Instance:**
   - Launch an EC2 instance (t2.medium or small) with Ubuntu.
   - Allow inbound traffic on ports 8080 and 22 in the security group.
   - Securely configure SSH access.

2. **Install Jenkins:**
   - Update packages and install Jenkins.
   - Install necessary plugins like JDK and SonarQube Scanner.

3. **Install Docker:**
   - Install Docker and add your user to the Docker group.
   - Reload Docker for changes to take effect.

4. **Install Trivy Scanner:**
   - Install Trivy for image vulnerability scanning.

5. **SSH into the Repository:**
   - Create an SSH key pair and add the public key to your GitHub account.
   - Clone the GitHub repository with your Go application code.

6. **Install Terraform, kubectl, and AWS CLI:**
   - Install Terraform, kubectl, and AWS CLI on your EC2 instance.

7. **Use Terraform to Create the Kubernetes Clusters:**
   - Initialize Terraform, plan, and apply to create AWS EKS clusters.

8. **Update Kubeconfig:**
   - Use AWS CLI to update the `kubeconfig` file for EKS cluster access.

9. **Create a Deployment.yaml File:**
   - Create a Kubernetes deployment configuration file (`deployment.yaml`) for your Go application.

## Jenkins Pipeline

The Jenkins pipeline is configured in the `Jenkinsfile` within your project. It consists of several stages, including:

- Git Checkout
- Build Docker Image
- Docker Image Scan
- Push to DockerHub
- Stop Docker Containers
- Kubernetes Deployment

You can customize this pipeline script to suit your project's specific requirements and naming conventions.

To execute the pipeline, create a Jenkins pipeline project and configure it to use the pipeline script in your project repository.

## Accessing the Application

After a successful deployment, you can access your Go application through the Load Balancer's external IP provided by AWS EKS.

## Maintenance and Troubleshooting

- Regularly update your infrastructure and dependencies.
- Secure your Jenkins server and credentials.
- Monitor and log your Jenkins pipeline for troubleshooting and improvement.
- Refer to the project's documentation for known issues and troubleshooting tips.

For questions or support, contact [Your Name or Contact Information].

Happy Deploying!
