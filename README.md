# django-postgreSQL-compose-jenkinspipeline

1. Deploy a Django app with Jenkins pipeline on a VM (Docker-Compose)

Infrastructure setup:

2 VMs - Jenkins server and App server

ii. Jenkins server:

Jenkins installed

Java (OpenJDK 11+)

Docker

Git

Let's start:

1. Start the VM's
2. File structure in GitHub:

(root)

Dockerfile

docker-compose.yml

Jenkinsfile

.env

3. Manual installation on each machine:

i) Jenkins server setup (192.168.56.xx)

Install Java

Install Jenkins

Install Docker (for building images)

Get Jenkins Admin password: -> Access Jenkins at http://192.168.56.xx:8080

ii) App server setup (192.168.56.xx)

Install Docker (for running containers)

4. Configure SSH Keys

i) On Jenkins server: generate ssh keys and copy them to app-server

ssh-keygen -t rsa -b 4096 -f ~/.ssh/id_rsa -N ""
ssh-copy-id vagrant@192.168.56.xx # App server (मा copy गरेको)

Test ssh access:
ssh vagrant@192.168.56.xx # should connect without password

5. Jenkins pipeline setup:

i. Access Jenkins UI (http://192.168.56.xx:8080)

ii. Install Plugins -> Docker Pipeline, Git, SSH Agent

iii. Create a New Pipeline Job:

Select pipeline script from SCM

Use your Git repo

Set branch to main/jenkins-pipeline

Use your Jenkinsfile

6. Run the pipeline & verify:

i. Trigger the Jenkins job manually

ii. Check deployment