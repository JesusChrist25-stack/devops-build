pipeline {
    agent any
    environment {
        DOCKER_IMAGE= 'pradeep905/devops'
        DOCKER_RESGISTRY= 'docker.io'
        DOCKER_USERNAME= 'pradeep905'
        DOCKER_PASSWORD= 'Mothermary@25'
        IMGAE_NAME= 'react-app'     
    }   
    stages {
        stage('Pulling the code from the git') {
            steps {
                git branch: 'main', credentialsId: 'Git', url: 'https://github.com/JesusChrist25-stack/devops-build.git'
            }
        }
        stage('Checking the Docker and Login') {
            steps {
                sh 'docker --version'
                sh 'docker login --username \$DOCKER_USERNAME -p \$DOCKER_PASSWORD'
            }
        }
        stage('Build and Deploy') {
            steps {
                sh 'chmod +x build.sh'
                sh './build.sh'
            }
        }
        stage('Pushing the image to Docker') {
            steps {
                sh 'docker tag \$IMGAE_NAME \$DOCKER_IMAGE:\$BUILD_NUMBER'
                sh 'docker push \$DOCKER_IMAGE:\$BUILD_NUMBER ' 
            }
        }
    }
}
