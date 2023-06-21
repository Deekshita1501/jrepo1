pipeline {
    agent any
    tools {
        git 'Default'
    }
    options {
        buildDiscarder(logRotator(numToKeepStr: '5'))
    }
    environment {
        DOCKERHUB_CREDENTIAL = credentials('dockerhub user')
    }

    stages {
        stage('build') {
            steps {
                sh 'sudo docker build -t deekshita87/testrepo2:testimg1 .'
            }
        }
        stage('Push') {
            steps {
                sh 'sudo echo $DOCKERHUB_CREDENTIAL_PSW | docker login -u $DOCKERHUB_CREDENTIAL_USR --password-stdin'
                sh 'sudo docker push deekshita87/testrepo2:testimg1'
            }
        }
    }
}
