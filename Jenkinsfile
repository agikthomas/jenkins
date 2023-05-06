pipeline {
    agent any
    environment {
        PATH = "/usr/bin/mvn:$PATH"
    }
    stages {
        stage("Git Checkout") {
            steps{
               git 'https://github.com/javahometech/myweb'
            }
        }
        stage("Maven build") {
            steps {
                sh "mvn clean package"
            }
        }
        stage("Check status of run") {
            sshagent(['service-integration-sdh-1']) {
                sh """
                   ssh -o StrictHostKeyChecking=no elastic-package status
                """
            }
        }    
    }
}
