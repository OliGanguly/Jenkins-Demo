Sample file for Jenkis demo
## Chain Jobs
Create Jobs -> go to specific job -> configure ->post build ->build other project ->choose ->save
make this chain for others as well

Manage -> Pugins ->Build pipeline(install) -> 

Dashboard -> + -> Build Pipeline view -> Name -> Select Initial Job -> No Of Displayed Builds -> No ->Save 

 * Yellow = in progress
 * Blue = Yet to be done
 * Green = executed

![demo](https://github.com/OliGanguly/Jenkis-Demo/assets/82031303/b42d600f-0c0e-4994-8905-691e371c1bef)

## Jenkis Pipeline
* Pipeline = [Dev -> Application Test -> Integration Test -> Acceptance Test -> Production]
  we have a pipeline here all the jobs/ processes are linked with each other , That is one runs after the other
  they all executed with a automatic trigger . so id dev job is successfull it automatically runs test job and so on..
 * Jenkis Pipeline - I s a Way to implement ci cd , all jobs starting from Build to deploye to test to release can be chained with each other .
 * JenkinsFile - To implement Jenkins Pipeline we use jenkins file, is a pipeline as a code.[Write Script ]
  ## Steps
   Step 1 : Start Jenkins

   Step 2 : Install Pipeline Plugin [Manage -> Pulgin]

   Step 3 : Create A New Job Name it type should be Pipeline

   Step 4 : PipeLine Section

            PipeLine Script -> Declerative Format  -> Write Code -> Apply ->Save

   Step 5 : Build Now

   ![JenkinsPipeline](https://github.com/OliGanguly/Jenkis-Demo/assets/82031303/f38e12d6-d08a-4bd6-85b8-756a91f8154d)

   ## Jenkis Pipeline | Get Jenkins File From Git 

   Step 1 : Create a new Job or use Existing Job (Type: Pipeline )

   Step 2 : Go to Configure -> Pipeline Section -> Choose SCM Script

   Step 3 : Create A file in github repo , with name jenkinsFile or what ever and provide  repo url , credential , Filename , Branch name ->Save 

   Step 4 : Build

   ![Output](https://github.com/OliGanguly/Jenkis-Demo/assets/82031303/0b5e4126-8a73-4dd3-b58a-a88f03725b7b)

  ## Declerative CICD Pipeline :
  * Create a Instance in aws connect with ssh
  ![pic1](https://github.com/OliGanguly/Jenkis-Demo/assets/82031303/bf5a2b10-c568-4d63-b9ae-a05bc84f6a06)

  * git clone "url"// clone project from github
  * cd go to your project folder [ code folder ]
  * sudo apt-get update //update 
  * sudo apt install docker.io // install docker -apt[application package manager ] , give super user power - sudo
  * docker --version
  * docker ps //running this command gives you a list of running containers 
    //get permission denied error
    ## solving
    * whoami //ubantu
      //ubantu does not has docker permission
    * sudo usermod -a -G docker @USER // modify user oermission append in a group of docker, add ubantu user in docker group
    * sudo reboot

 Docker will prepare a build 
 # All this things will automated by 
 * docker build -t app_name . //docker file build Image and Image build Docker Container
 
 ![dockerFile](https://github.com/OliGanguly/Jenkis-Demo/assets/82031303/17746766-d050-4256-9913-76a43dadabb2)
  
* cat DockerFile
* Image directory would be /app/backend [current dir]
* copy requirments.txt to app/backend ->requirements has all dependencies to run this project 
* run pip install -r requirments.txt pip->python package installer

## INstall Jenkins
* sudo apt install openjdk-11-jre [Install java]
* java -version
* 6.go to jenkins website
https://www.jenkins.io/doc/book/installing/linux/
copy Installation command
Like :
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
* sudo apt-get update
* sudo apt-get install jenkins
* systemctl status jenkins //status of jenkins
* Try to connect:
public-ip:8080
Like - http://3.145.75.211:8080

* go to Ec2 Instance
Edit security Group
Add One group [ Add Role ]
Custom TCP ------Port 8080 ---- source - MY IP [ I will access Jenkis server through my IP only ]

![addSecurityGroup](https://github.com/OliGanguly/Jenkins-Demo/assets/82031303/f95d4cbf-be40-48f3-a56f-6b7671c2bc5d)
Add Incoming Security Rule [my ip ]
My Ip will get access of my aws ec2 server
![createAdminUser](https://github.com/OliGanguly/Jenkins-Demo/assets/82031303/d7161483-0842-42f9-bad0-240d2d575fdd)

Unlock Jenkins
Get password
![jenkinsapp](https://github.com/OliGanguly/Jenkins-Demo/assets/82031303/751119d0-bd96-45be-8b80-ce7a2654aad5)

10.sudo cat "file path to see the passpowd" .
11.Install Suggested Plugin
![installPlugin](https://github.com/OliGanguly/Jenkins-Demo/assets/82031303/5156349a-1d7e-426e-888d-42b9193c6701)

* Create job [ Freestyle , Pipeline ]
* I choose Pipeline
  ![jenkis-pipeline](https://github.com/OliGanguly/Jenkins-Demo/assets/82031303/f3b38533-a19b-4a14-b3cc-3e0a0eb580d6)\

* Give Description
* Add Github Projects //Copy url from github
  ![addGithubLink](https://github.com/OliGanguly/Jenkins-Demo/assets/82031303/aa89163a-f894-48b1-ac6f-47590bc4b748)

* Build Trigger -> Github Hook Trigger [ triggered with commit ]

 ## Script [ Pipeline come from code ]
 * Agents is a runnin machine where you can run your code .
 * Jenkins assign task to agents 
 PipeLine{

 agents any //give task to agents [Running machine]

## Installation

Install my-project with npm

```bash
pipeline{
agents any
stages{
stage("Code"){
 steps{
            echo "Cloning The Code"  
            git url:"https://github.com/OliGanguly/django-notes-app.git",branch:"main"
      }
}
stage("Build"){
steps{
             echo "Building The Code"  ,
             sh "docker build -t note-application ."
      } 
}
stage("Push To Docker Hub"){
}
stage("Deploy"){
}
}
}
```
## Build Fail
![ErrorComes](https://github.com/OliGanguly/Jenkins-Demo/assets/82031303/5acfc990-6f8d-4fd0-95bb-3bd151501dcd)

* Solution [ add user in docker group ]
* Server
* cd /var/lib/jenkins/workspace/note-app-cicd'
* sudo usermod -aG docker jenkins
* sudo reboot
* Build again
  //So note-application image is with you -> Push to Docker Hub
* create account in hub.dockerhub.com
  ![DockerHub](https://github.com/OliGanguly/Jenkins-Demo/assets/82031303/d76091e2-663e-48d7-9400-6e7e339a0e83)
terminal -> doker login

![dockerHubLogin](https://github.com/OliGanguly/Jenkins-Demo/assets/82031303/fe79376f-a0cd-4b38-ab1a-719642f5c1f3)


  
 

##Deploy   

  



    


    







 
  

  


    
   

  

   


             


