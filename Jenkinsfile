pipeline {
    agent any
    // agent {
    //     docker {
    //         image 'docker:latest'
    //         args '-v /var/run/docker.sock:/var/run/docker.sock'
    //     }
    // }
    environment{
        DOCKERHUB_CREDENTIAL=credentials('hoatoi-dockerhub')
    }

    stages{
        stage('Clone'){
            steps{
                git branch: 'main', url: 'https://github.com/vohoatoi147/jenkins1.git'

            }

        }
        stage('Build'){
            steps{
                sh 'docker build -t vohoatoi147/test-jenkins:v1 .'
                sh 'echo $DOCKERHUB_CREDENTIAL_PWS | docker login -u $DOCKERHUB_CREDENTIAL_USR --password-stdin'
                sh 'docker push vohoatoi147/test-jenkins:v1'
            }
        }
    }
}