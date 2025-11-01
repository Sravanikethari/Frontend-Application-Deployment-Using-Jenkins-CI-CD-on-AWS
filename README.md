# Frontend-Application-Deployment-Using-Jenkins-CI-CD-on-AWS
## Description
In today’s fast-paced software development landscape, Continuous Integration and Continuous Deployment (CI/CD) play a crucial role in accelerating application delivery and improving reliability.
This project demonstrates how to automate the deployment of a Java-based application to an Apache Tomcat server using a Jenkins-powered CI/CD pipeline.
The workflow leverages Git for version control and Maven for build management, ensuring a seamless, repeatable, and production-ready release process.

## Understanding the Tools

•	GIT- A distributed version control system used to store your application code, collaborate efficiently, and track changes across development teams.

•	Maven - A powerful build automation and dependency management tool for Java projects, ensuring consistent and reproducible builds.

•	Jenkins - The heart of the CI/CD pipeline, automating code build, test, and deployment processes to streamline delivery and reduce manual effort.

•	Apache Tomcat - A lightweight, reliable application server for deploying and running Java-based web applications in production environments.


<img width="1542" height="1088" alt="image" src="https://github.com/user-attachments/assets/c3c7b01d-3b0f-4286-9551-71be49a9960b" />

## Practical Use Case
Consider a team developing an e-commerce web app. Each time a developer modifies the product catalog, the change is pushed to GitHub — instantly activating the automated CI/CD workflow.
Here’s what happens next:

1) Jenkins automatically pulls the latest code from GitHub.

2) Maven builds the application and runs unit tests to validate code integrity.

3) On successful testing, Jenkins deploys the updated build to the Apache Tomcat server.

This fully automated workflow eliminates manual intervention, reduces deployment time, and ensures the application is always up-to-date, stable, and ready for users.

## Step by step  Deployment of Frontend Application Using Jenkins CI/CD on AWS

# STEP-1: Launch 2 EC2 Instances (Kernel 5.10)

Jenkins Server

Tomcat Server

<img width="2386" height="426" alt="image" src="https://github.com/user-attachments/assets/192ba84d-0b4d-4dfa-8b4e-ad31538b42da" />

# STEP-2: Connect Jenkins server and Install Jenkins & GIT
#STEP-1: INSTALLING GIT
yum install git -y

#STEP-2: GETTING THE REPO (jenkins.io --> download -- > redhat)


yum install java-17-amazon-corretto -y
yum install jenkins -y

#STEP-4: RESTARTING JENKINS (when we download service it will on stopped state)
systemctl start jenkins.service
systemctl status jenkins.service
