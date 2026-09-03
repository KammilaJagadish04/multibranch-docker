pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image2 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image2 shaikmustafa/paytm:bus'
            }
        }
       
        stage('push') {
            steps {
               withDockerRegistry(credentialsId: 'docker_hub') {
    // some block
                }
            }
        }
    
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bus-app -p 2222:80 shaikmustafa/paytm:bus'
            }
        }
    }
}
