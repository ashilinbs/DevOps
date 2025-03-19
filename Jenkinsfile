pipeline {
    agent any

    stages {
        stage('SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/ashilinbs/DevOps.git'
            }
        }

        stage('Build') {
            steps {
                bat "mvn clean"
                bat "mvn install"
            }
        }

        stage('Build to Images') {
            steps {
                script {
                    bat 'docker build -t ashilin04/simplewebapp .'
                }
            }
        }

        stage('Push to Hub') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'cred', url: 'https://index.docker.io/v1/') {
                        bat 'docker push ashilin04/simplewebapp'
                    }
                }
            }
        }
    }
}
