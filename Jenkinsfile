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
                sh 'sh docker-compose exec app chmod 777 /var/www/composer.lock'
                sh 'docker-compose run app rm -rf vendor composer.lock'
                sh 'docker-compose run app composer install'
                sh 'docker-compose run app php artisan key:generate'
            }
        }
    }
}
