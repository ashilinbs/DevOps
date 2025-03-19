pipeline {
    agent any

    stages {
        stage('scm') {
            steps {
        git branch: 'main', url: 'https://github.com/ashilinbs/DevOps.git'
            }
        }
        stage('build') {
            steps {
               bat "mvn clean"
               bat "mvn install"
}
}
stage('build to images') {
            steps {
               script{
                  bat 'docker build -t ashilin04/simplewebapp .'
               }
    }
}
stage('push to hub') {
            steps {
               script{
                 withDockerRegistry(credentialsId: 'cred', url: 'https://index.docker.io/v1/') {
                  bat 'docker push ashilin04/simplewebapp'
               }
            }
            }
}
}
