pipeline {
    agent any
    environment {
        PATH = "/usr/bin/mvn:$PATH"
    }
    stages {
//         stage("Git Checkout") {
//             steps{
//                git 'https://github.com/javahometech/myweb'
//             }
//         }
//         stage("Maven build") {
//             steps {
//                 sh "mvn clean package"
//             }
//         }
        stage("Check status of run") {
            environment {
                PATH="/home/agikthomas:$PATH"
            }
            steps {
                sshagent(['service-integration-sdh-1']) {
                    sh """
                       ssh -o StrictHostKeyChecking=no -l agikthomas 10.160.0.4 elastic-package status
                    """
                }
            }
        }    
    }
}
