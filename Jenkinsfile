pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                checkout scm
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                sh 'docker-compose build app'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                sh 'docker-compose up -d'
                sh 'docker-compose run app ls -l'
                sh 'docker-compose run app php artisan key:generate'
            }
        }
    }
}
