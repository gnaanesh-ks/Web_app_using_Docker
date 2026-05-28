pipeline {
    agent any

    stages {

        stage('Clone Repo') {
            steps {
                git url: 'https://github.com/gnaanesh-ks/Web_app_using_Docker.git',
                    branch: 'main',
                    credentialsId: 'gitid'
            }
        }

        stage('Build') {
            steps {
                sh 'docker compose build'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker compose down'
                sh 'docker compose up -d'
            }
        }

        stage('Done') {
            steps {
                echo 'App is running on port 5000'
            }
        }
    }

    post {
        failure {
            echo 'Build failed!'
        }
    }
}
