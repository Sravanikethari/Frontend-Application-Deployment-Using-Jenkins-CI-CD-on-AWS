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

<img width="1523" height="364" alt="instance" src="https://github.com/user-attachments/assets/bf225a49-8aec-4a74-9b59-7b55ad38dcd2" />

# STEP-2: Connect Jenkins server and Install Jenkins & GIT

- <a href="https://github.com/Sravanikethari/Frontend-Application-Deployment-Using-Jenkins-CI-CD-on-AWS/blob/main/GIT%20&%20Jenkins%20setup">GIT & Jenkins setup</a>


<img width="1889" height="868" alt="dashboard" src="https://github.com/user-attachments/assets/c3a491fe-238e-4a21-9ac7-36fcae7d5e82" />

Now copy the public-ip of your system and access it with 8080 port.

# STEP-3: Install the Deploy to Container plugin to enable application deployment.

Go to Manage Jenkins » Plugins » Available Plugins » Deploy to container

<img width="1920" height="865" alt="deploy-to-cntr" src="https://github.com/user-attachments/assets/7a389869-2ad7-4988-a8b2-5a269251f33a" />

# STEP-4: Configure Maven Integration

Go to Manage Jenkins » tools and select maven

under the Maven Installations click on Add Maven

Name: mymaven

Version: default (3.9.11)


<img width="1897" height="862" alt="mymaven" src="https://github.com/user-attachments/assets/ee13595b-d49c-4362-9934-f97000ff0680" />
Now click on save

# STEP-5: New Freestyle Job Configuration


<img width="1889" height="868" alt="dashboard" src="https://github.com/user-attachments/assets/e6138bdb-7919-4e69-ad63-01ce8afb30f7" />



<img width="1889" height="867" alt="git-url" src="https://github.com/user-attachments/assets/5e4b72e8-02e4-4a83-a0eb-a9be5567231a" />

Go to Build Steps and select Invoke top-level Maven targets and select the Maven version as mymaven

Now enter the goal as clean package


<img width="1894" height="868" alt="clean-package" src="https://github.com/user-attachments/assets/323577da-28b0-4893-876a-ddd3ebeac35f" />

Save the job and click on Build Now


<img width="1092" height="824" alt="build-sucess" src="https://github.com/user-attachments/assets/20a657a5-194e-4d64-8a35-27d44d57bb71" />
If the build gets success, go to workspace and open the target folder, we will get war file


<img width="1634" height="872" alt="workspace-target" src="https://github.com/user-attachments/assets/965e72a4-84ae-4bfe-8de4-1d6f43224be5" />

# STEP-6: Deploy the application on Tomcat Server

connect the tomcat server and run the script to setup tomcat

Run the below script to setup tomcat

- <a href="https://github.com/Sravanikethari/Frontend-Application-Deployment-Using-Jenkins-CI-CD-on-AWS/blob/main/Deploy%20the%20application%20on%20Tomcat%20Server.html">Tomcat</a>

Remember the tomcat credentials
•	username : tomcat
•	password : admin@123
If you wish to modify, change the credentials on above script also.
Now access the tomcat dashboard with public-ip of tomcat server with 8080 port.

<img width="1920" height="940" alt="tomcat-homepage" src="https://github.com/user-attachments/assets/6919e019-03a7-459e-8fb4-1a4c01b4c917" />

Now go to Manager App and enter the credentials, You will get the Tomcat Web Application Manager dashboard.

<img width="1920" height="934" alt="tomcat-application-manager" src="https://github.com/user-attachments/assets/dbb6fd65-87b9-43bc-9001-3b13847a5f52" />


# STEP-7: Integrate Tomcat with Jenkins

Configure the Jenkins job and select Post Build Actions and select Deploy war/ear to a container

WAR/EAR file: target/*.war

context path: swiggy

<img width="1891" height="875" alt="war-ear" src="https://github.com/user-attachments/assets/70c3c520-9cca-48c7-b090-a7c8b76d8714" />

and click on add container and select Tomcat 9.x Remote

<img width="1894" height="869" alt="9 x" src="https://github.com/user-attachments/assets/f0dd67a8-b4e3-4bc9-b25b-010f923c6d45" />
Now add the tomcat credentials, click on Add select Jenkins

<img width="1252" height="750" alt="tom-1" src="https://github.com/user-attachments/assets/262c3004-f50a-4ede-998c-19ddb3b89e68" />

<img width="1250" height="744" alt="tom-2" src="https://github.com/user-attachments/assets/3f83d072-8017-4a7f-8bf9-4a7720db0e90" />


Now click on Add and select the credentials and enter the tomcat url

<img width="1891" height="863" alt="tomcat-url" src="https://github.com/user-attachments/assets/de622abf-336a-486f-85aa-8eb75536e43c" />

Now save the job and click on Build Now, If the build gets success then our application will be deployed on tomcat successfully.

<img width="1007" height="865" alt="2nd-deploy-status" src="https://github.com/user-attachments/assets/9ceeb14a-ddf4-4db1-8c1d-39fd001b9c29" />

The build is success, Now lets refresh the tomcat page and we will see swiggy app is running


<img width="1888" height="946" alt="swiggy" src="https://github.com/user-attachments/assets/3a25d27f-7064-475b-9ad7-c13ada5da0cb" />

Open the swiggy app and check the output.

To automate the delivery process, we can also implement Webhooks!.

# Best Practices
•	Maintain a dedicated staging environment to thoroughly test deployments before moving them to production.

•	Integrate automated testing into your CI/CD pipeline to identify and resolve issues early.

•	Harden Jenkins and Tomcat configurations with proper authentication, access controls, and regular security updates.


# Conclusion
Automating deployments with a CI/CD pipeline helps you save time, minimize errors, and accelerate feature delivery. Deploying Java applications to Tomcat using Jenkins and Maven becomes seamless when approached methodically.
Adopting CI/CD streamlines workflows, enhances reliability, and accelerates feature delivery—allowing teams to focus on innovation over manual tasks.

# 👨‍💻 Author & Support🛠️
This project is maintained by Sravani💡. Your feedback and contributions are welcome!

# 📧 Connect with me:

GitHub: https://github.com/Sravanikethari

LinkedIn: https://linkedin.com/in/sravani-k-082838350

# ⭐ Support the Project
If you found this project helpful, please consider:


•	Starring ⭐ the repository

•	Sharing it with your network

•	Contributing to its improvement

