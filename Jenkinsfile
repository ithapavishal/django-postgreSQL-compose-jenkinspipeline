pipeline {
    agent any

    environment {
        dockerImage = "thapavishal/jenkins-django-compose-pipeline"
    }

    stages {
        stage('Checkout from GitHub') {
            steps {
                git url: 'https://github.com/ithapavishal/django-postgreSQL-compose-jenkinspipeline.git', branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $dockerImage .'
            }
        }

        // stage('Push to Docker Hub') {
        //     steps {
        //         withCredentials([string(credentialsId: 'docker-hub-pass', variable: 'DOCKER_HUB_PASS')]) {
        //             sh 'echo $DOCKER_HUB_PASS | docker login -u your-dockerhub-username --password-stdin'
        //             sh 'docker push $dockerImage'
        //         }
        //     }
        // }

        stage('Deploy on App VM') {
            steps {
                sh 'ssh vagrant@192.168.56.11 "docker pull $dockerImage && docker-compose -f /home/vagrant/django-app/docker-compose.yml up -d --build"'
            }
        }
    }
}