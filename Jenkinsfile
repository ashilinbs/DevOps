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
                sh "mvn clean"
                sh "mvn install"
            }
        }

        stage('Build to Images') {
            steps {
                script {
                    sh 'docker build -t ashilin04/simplewebapp .'
                }
            }
        }

        stage('Push to Hub') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'cred', url: 'https://index.docker.io/v1/') {
                        sh 'docker push ashilin04/simplewebapp'
                    }
                }
            }
        }
    }
}
