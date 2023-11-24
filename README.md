# Compozent-Basic-task-2 - Jenkins pipeline, docker , git with AWS ECR

## Install Jenkins

https://www.jenkins.io/doc/tutorials/tutorial-for-installing-jenkins-on-AWS/

Step 1 – Create theEc2 instancein AWS account with these parameters.

    +EC2type–Ubuntut2.medium
    +EBSvolume–30GB
    +Region–US-EAST-1

<img width="400" height="400" src=https://github.com/tohidhanfi20/Compozent-Basic-task-2/blob/main/Screenshots/ubuntu%20instance.png>




Launch your Instance

Then use this commands to setup your jenkins server
     
     #!/bin/bash

    sudo apt update -y

    sudo apt upgrade -y 

    sudo apt install openjdk-17-jre -y

    curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
    /usr/share/keyrings/jenkins-keyring.asc > /dev/null
    echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
    https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
    /etc/apt/sources.list.d/jenkins.list > /dev/null
    sudo apt-get update -y 
    sudo apt-get install jenkins -y

              |
               | 
                |
                 |

<img width="1000" height="600" src=https://github.com/tohidhanfi20/Compozent-Basic-task-2/blob/main/Screenshots/jenkins%20command.png>










<img width="1000" height="600" src=https://github.com/tohidhanfi20/Compozent-Basic-task-2/blob/main/Screenshots/jenkins%20server.png>



### Plugins to install in Jenkins

1. Pipeline: AWS Steps
2. CloudBees AWS Credentials
3. All Git
4. Amazon ECR Pipeline
5. Docker API
6. Docker Commons
7. Docker Pipeline
8. Docker
9. Docker workflow



<img width="1200" height="600" src=https://github.com/tohidhanfi20/Compozent-Basic-task-2/blob/main/Screenshots/Manage%20Plugins.png>

   
## Perform these commands on the EC2 instance

##Install in Amazon Ubuntu

    #!/bin/bash
    sudo apt update -y

    sudo apt install apt-transport-https ca-certificates curl software-properties-common -y

    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

    sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable" -y

    sudo apt update -y

    apt-cache policy docker-ce -y

    sudo apt install docker-ce -y

    #sudo systemctl status docker

    sudo chmod 777 /var/run/docker.sock

    sudo apt install git





GitHub Integration Plugin
Version0.5.0
GitHub Integration Plugin for Jenkins


GitHub plugin
Version1.37.0
This plugin integrates GitHub to Jenkins.
Report an issue with this plugin


Pipeline: GitHub
Version2.8-138.d766e30bb08b

## Configure jenkins with git
 DO this command to get path of git this server
 So that it can be added in JENKINS DASHBOARD

 
 which git  ---  paste this path to jenkins

 <img width="600" height="200" src=https://github.com/tohidhanfi20/Compozent-Basic-task-2/blob/main/Screenshots/which%20git.png>


## NOW setup ECR in your amazon console


<img width="1600" height="400" src=https://github.com/tohidhanfi20/Compozent-Basic-task-2/blob/main/Screenshots/ECR%20dashboard.png>


# MAKE PRIVATE REPO
    --  Give name 
        Make repo
save your credentials so that it can be updated in jenkinsfile
             
    like ECR URI ID and repository name

<img width="1400" height="300" src=https://github.com/tohidhanfi20/Compozent-Basic-task-2/blob/main/Screenshots/Screenshot%202023-11-24%20115741.png>


Add webhook to github
with your jenkins url

example:- http://youripwithport8080/github-webhook/


<img width="600" height="200" src=https://github.com/tohidhanfi20/Compozent-Basic-task-2/blob/main/Screenshots/Add%20webhook.png>


# Create your pipeline

<img width="1400" height="300" src=https://github.com/tohidhanfi20/Compozent-Basic-task-2/blob/main/Screenshots/first%20pipeline.png>

Then add git crendials to access your code and jenkins file

<img width="1400" height="300" src=https://github.com/tohidhanfi20/Compozent-Basic-task-2/blob/main/Screenshots/add%20git%20repo%20to%20jenkins.png>

Then set Git triggers in Jenkins pipeline

<img width="1400" height="300" src=https://github.com/tohidhanfi20/Compozent-Basic-task-2/blob/main/Screenshots/git%20triggers.png>

Then Build NOW which starts your pipeline

<img width="1400" height="300" src=https://github.com/tohidhanfi20/Compozent-Basic-task-2/blob/main/Screenshots/Build%20Now.png>

Then Image is pushed to ECR 

<img width="1400" height="300" src=https://github.com/tohidhanfi20/Compozent-Basic-task-2/blob/main/Screenshots/images%20pushed%20to%20ECR.png>

Finally Our BUILD is successful now

<img width="1400" height="300" src=https://github.com/tohidhanfi20/Compozent-Basic-task-2/blob/main/Screenshots/Build%20Success.png>

NOW we have pipeline working in JENKINS DASHBOARD with the name MAIN PROJECT

<img width="1400" height="300" src=https://github.com/tohidhanfi20/Compozent-Basic-task-2/blob/main/Screenshots/Main%20project.png>










