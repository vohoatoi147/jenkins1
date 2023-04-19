pipeline {
    agent any
    environment{
        DOCKERHUB_CREDENTIAL=credentials('hoatoi-dockerhub')
    }

    stages{
        stage('Clone'){
            steps{
                git branch: 'main', url: 'https://github.com/vohoatoi147/jenkins1.git'
                sh 'docker build -t vohoatoi147/test-jenkins:v1 .'
            }

        }
        stage('login'){
            steps{
                sh 'echo $DOCKERHUB_CREDENTIAL_PWS | docker login -u $DOCKERHUB_CREDENTIAL_USR --password-stdin'
            }
        }
        stage('Build'){
            steps{
                sh 'docker push vohoatoi147/test-jenkins:v1'
            }
        }
    }
}