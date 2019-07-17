#!/usr/bin/env groovy
pipeline{
    agent { dockerfile true }
    stages{
        stage('build') {
            steps {
                checkout scm

                sh "composer install"
                sh "cp .env.example .env"
                sh "php artisan key:generate"
            }
        }

        stage('test') {
            steps {
                sh "./vendor/bin/phpunit"
            }
        }

        stage('deploy') {
                // ansible-playbook -i ./ansible/hosts ./ansible/deploy.yml
            steps {
                sh "echo 'WE ARE DEPLOYING'"
            }
        }
    }
}
 