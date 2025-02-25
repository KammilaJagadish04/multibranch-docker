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
                sh 'docker tag image1 shaikmustafa/paytm:bank'
            }
        }
        stage ("Push") {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerhub') {
                        sh 'docker push shaikmustafa/paytm:bank'
                    }
                }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bank-app -p 7777:80 shaikmustafa/paytm:bank'
            }
        }
    }
}
