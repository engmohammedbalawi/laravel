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
               
                sh 'docker-compose up -d'  // Use the sh step to execute the shell command
                sh 'docker-compose exec app rm -rf vendor composer.lock'
                sh  'docker-compose exec app composer install'
                sh    'docker-compose exec app php artisan key:generate
'
            }
        }
    }
}
