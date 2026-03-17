pipeline {
    agent any

    environment {
        IMAGE = "2023bcs0029rinu/2023bcs0029"
    }

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/rinuannvarghese05-bit/devops-lab.git'
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t $IMAGE .'
            }
        }

        stage('Login') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub',
                    usernameVariable: 'USER',
                    passwordVariable: 'PASS'
                )]) {
                    sh 'echo $PASS | docker login -u $USER --password-stdin'
                }
            }
        }

        stage('Push') {
            steps {
                sh 'docker push $IMAGE'
            }
        }
    }
}
