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

- <a href="https://github.com/Sravanikethari/Frontend-Application-Deployment-Using-Jenkins-CI-CD-on-AWS">Install jenkins & git</a>

Now copy the public-ip of your system and access it with 8080 port.


![web](https://github.com/user-attachments/assets/97c8a9ce-fb80-4356-a4a6-a0fd1be16fa7)

# STEP-3: Now Install Deploy to container plugin

Go to Manage Jenkins » Plugins » Available Plugins » Deploy to container


<img width="2880" height="764" alt="image" src="https://github.com/user-attachments/assets/dd848c8e-7c27-492b-8c27-89ac098f76bd" />

# STEP-4: Integrate Maven

Go to Manage Jenkins » tools and select maven

under the Maven Installations click on Add Maven

Name: mymaven

Version: default (3.9.9)


<img width="2846" height="1542" alt="image" src="https://github.com/user-attachments/assets/29126666-f19c-460d-91d9-111fb375bd70" />
Now click on save

# STEP-5: Create a Free Style Job


<img width="2878" height="1574" alt="image" src="https://github.com/user-attachments/assets/f8ec739b-f839-4e7f-ad95-eca6a9e48a1c" />
Go to Source Code Management and select Git and enter the repo-url (https://github.com/usubbu/one.git)


<img width="2880" height="1382" alt="image" src="https://github.com/user-attachments/assets/abb0c1ff-d39f-4457-b984-6c815b9ffcd3" />

Go to Build Steps and select Invoke top-level Maven targets and select the Maven version as mymaven

Now enter the goal as clean package


<img width="2874" height="1566" alt="image" src="https://github.com/user-attachments/assets/be7d351e-59fe-4501-92ad-7f72466b7204" />

Save the job and click on Build Now


<img width="1302" height="1094" alt="image" src="https://github.com/user-attachments/assets/5c2a28a0-44b9-4e86-ae74-8e00fa9b1063" />
If the build gets success, go to workspace and open the target folder, we will get war file


<img width="1898" height="1140" alt="image" src="https://github.com/user-attachments/assets/a5d3fa60-4116-444a-9663-91f13698e2b9" />

# STEP-6: Deploy the application on Tomcat Server

connect the tomcat server and run the script to setup tomcat

Run the below script to setup tomcat

- <a href="https://github.com/Sravanikethari/Frontend-Application-Deployment-Using-Jenkins-CI-CD-on-AWS/blob/main/Deploy%20the%20application%20on%20Tomcat%20Server.html">Tomcat</a>

Remember the tomcat credentials
•	username**:** tomcat
•	password**:** admin@123
If you wish to modify, change the credentials on above script also.
Now access the tomcat dashboard with public-ip of tomcat server with 8080 port.

<img width="2852" height="1300" alt="image" src="https://github.com/user-attachments/assets/9e3bf9e6-3935-4d3b-955b-f2a43a6b1f4c" />
Now go to Manager App and enter the credentials, You will get the Tomcat Web Application Manager dashboard.

<img width="2880" height="1460" alt="image" src="https://github.com/user-attachments/assets/0c0fa523-7363-4456-835f-798d18932f7b" />

# STEP-7: Integrate Tomcat with Jenkins

Configure the Jenkins job and select Post Build Actions and select Deploy war/ear to a container

WAR/EAR file: target/*.war

context path: swiggy

<img width="2876" height="1568" alt="image" src="https://github.com/user-attachments/assets/6d1163d2-4495-4494-a121-5fd6fa148e6f" />

and click on add container and select Tomcat 9.x Remote

<img width="2860" height="1534" alt="image" src="https://github.com/user-attachments/assets/0e1f4a8f-9c6e-4f7f-9649-8ca0602b0a70" />
Now add the tomcat credentials, click on Add select Jenkins

<img width="2256" height="1430" alt="image" src="https://github.com/user-attachments/assets/be052c13-6ae2-4ff8-b67d-8241204562d1" />

Now click on Add and select the credentials and enter the tomcat url

<img width="2724" height="1550" alt="image" src="https://github.com/user-attachments/assets/09c3146e-7d58-4c81-b1b9-d962ad8ff0c8" />

Now save the job and click on Build Now, If the build gets success then our application will be deployed on tomcat successfully.

<img width="1594" height="1352" alt="image" src="https://github.com/user-attachments/assets/4992d8f3-600a-4a74-a7b3-49ddac7f5c6b" />

The build is success, Now lets refresh the tomcat page and we will see swiggy app is running


<img width="2870" height="1492" alt="image" src="https://github.com/user-attachments/assets/9a8ca7e3-1d3e-45b5-b4fd-e178cbea48ac" />

Open the swiggy app and check the output.

To automate the delivery process, we can also implement Webhooks!.

# Best Practices
•	Maintain a dedicated staging environment to thoroughly test deployments before moving them to production.
•	Integrate automated testing into your CI/CD pipeline to identify and resolve issues early.
•	Harden Jenkins and Tomcat configurations with proper authentication, access controls, and regular security updates.

# Conclusion
Automating deployments with a CI/CD pipeline helps you save time, minimize errors, and accelerate feature delivery. Deploying Java applications to Tomcat using Jenkins and Maven becomes seamless when approached methodically.
Adopting CI/CD streamlines workflows, enhances reliability, and accelerates feature delivery—allowing teams to focus on innovation over manual tasks.

🛠️ Author & Community
This project is maintained by Sravani💡. Your feedback and contributions are welcome!

📧 Connect with me:

GitHub: https://github.com/Sravanikethari
LinkedIn: https://linkedin.com/in/sravani-k-082838350
