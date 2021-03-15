# Final Project

## Description

In this project I'm implementing **CI/CD** using **Git, Jenkins, Ansible and Docker**. Developer will commit his changes to Git which triggers (Webhook) Jenkins pipline job, it pulls code from Github, builds the java application using Maven, builds Docker image and uploads it to Docker Hub, then usin Ansible playbook deploy Docker container to Web Server.

I'm using **Terraform** to create Jenkins and Web Servers, and to install required tool (Ansible, Docker, Git) on Jenkins Server.

![Image1p](screenshots/1p.jpg "schema")

## Creating infrastructure

Terraform is a tool for building, changing, and versioning infrastructure safely and efficiently. Using Terraform I'm creating two EC2 instances with security group sg1.

![Image2](screenshots/039.png "2")
![Image3](screenshots/037.png "3")

![Image4](screenshots/042.png "4")
![Image5](screenshots/041.png "5")

![Image6](screenshots/002.png "6")

![Image7](screenshots/003a.jpg "7")

## Configuring Jenkins

Navigating to Jenkins web interfase ( public IP of Jenkins Server, port 8080), entering password, creating first admin user, installing suggested plugins.

![Image8](screenshots/004a.jpg "8")

![Image9](screenshots/009.png "9")

Configuring tools and plugins in Jenkins. Navigating to Manage Jenkins > Global Tool Configuration and adding Maven (automatically installed by Jenkins), then adding Ansible Plugin (because from Jenkins wiil be executed Ansible playbook for deploying container to Web Server). 

![Image10](screenshots/010.png "10")
![Image11](screenshots/012.png "11")

![Image12](screenshots/011.png "12")

## Creating a Jenkins Pipeline job

I'm using Maven for java project to build .war file. After that I'm building Docker image ( using Tomcat as a base image), the .war file is added to this image at the Tomcat webapp location. 

![Image13](screenshots/014.png "13")

![Image14](screenshots/028.png "14")

![Image15](screenshots/029.png "15")

Docker file.

![Image185](screenshots/185.png "dockerfile")

Pipeline script (declarated pipeline):

```
properties([pipelineTriggers([githubPush()])])
node { git url: 'https://github.com/KhafazovPavlo/final_project.git', branch: 'master' }
pipeline{
    agent any
    tools {
      maven 'maven3'
    }
   
    stages{
        stage('SCM'){
            steps{
                git credentialsId: 'github', 
                    url: 'https://github.com/KhafazovPavlo/final_project'
            }
        }
        
        stage('Maven Build'){
            steps{
                sh "mvn clean package"
            }
        }
        
        stage('Docker Build'){
            steps{
                sh "docker build . -t pavelkhafazov/webapp:${BUILD_TAG} "
            }
        }
        
        stage('DockerHub Push'){
            steps{
                withCredentials([string(credentialsId: 'docker-hub', variable: 'dockerHubPwd')]) {
                    sh "docker login -u pavelkhafazov -p ${dockerHubPwd}"
                }
                
                sh "docker push pavelkhafazov/webapp:${BUILD_TAG} "
            }
        }
        
        stage('Docker Deploy'){
            steps{
              ansiblePlaybook credentialsId: 'dev-server', disableHostKeyChecking: true, 
                extras: "-e BUILD_TAG=${BUILD_TAG}", installation: 'ansible', inventory: 'web.inv', 
                    playbook: 'deploy-docker.yml'
            }
        }
    }
}
```
_BUILD_TAG is an environment variable (string of jenkins JOB_NAME-BUILD_NUMBER) for easier identification._

Configuring Git (to make pull from repository), by providing repository URL, branch, credentials.

![Image16](screenshots/016.png "16")

Adding credentials for Docker Hub (to be able push an image) using Snippet Generator withCredentials to bind credentials to variable.

![Image17](screenshots/017.png "17")
![Image18](screenshots/018.png "18")

Ansible playbook (to install python, Docker and run container)

![Image19](screenshots/086.png "19")

Configure Ansible tool.

![Image20](screenshots/022.png "21")
![Image21](screenshots/021.png "22")

Configuring Webhook (when push event is triggered, it'll send a HTTP POST payload to the webhook's configured URL of Jenkins Server to start pipeline job).

![Image23](screenshots/023.png "23")

Final Project structure.

![Image24](screenshots/043.png "24")

GitHub repository.

![Image25](screenshots/013.png "25")

Starting pipeline job.

![Image26](screenshots/023.png "26")

Commiting some changes to GitHub repository and job starts automatically.

![Image027](screenshots/026.png "27")

Result - java application build, created image with application and pushed to Docker Hub and then container ran on Web Server.

![Image028](screenshots/024.png "28")

Console output.

![Image029](screenshots/030.png "29")

Docker Hub.

![Image033](screenshots/033.png "33")

Jenkins console output log [link](jenkins_log.txt)

*Final Project repository* [link2](https://github.com/KhafazovPavlo/final_project)



















