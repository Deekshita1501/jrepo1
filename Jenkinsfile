pipeline {
    agent any
    tools {
        git 'Default'
    }
    options {
        buildDiscarder(logRotator(numToKeepStr: '5'))
    }
    environment {
        DOCKERHUB_CREDENTIAL = credentials('docker')
    }

    stages {
        stage('build') {
            steps {
                sh 'sudo docker build -t deekshita87/testrepo2'
            }
        }
        stage('Push') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIAL_PSW | docker login -u $DOCKERHUB_CREDENTIAL_USR --password-stdin'
                sh 'docker push deekshita87/testrepo2'
            }
        }
    }
}
