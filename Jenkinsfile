pipeline {
    agent {
        docker {
            image 'node:14'
            args '-u root'
        }
    }

    stages {
        stage('Klonowanie repozytorium') {
            steps {
                git branch: 'main', url: 'https://github.com/Szufrajda/Kolokwium-Jenkins.git'
            }
        }
        stage('Instalacja zależności') {
            steps {
                sh 'npm install'
            }
        }
        stage('Uruchamianie testów') {
            steps {
                sh 'npm test'
            }
            post {
                always {
                    junit 'test-results/*.xml'
                }
            }
        }
        stage('Lintowanie kodu') {
            steps {
                sh 'npm run lint'
            }
        }
    }
}
