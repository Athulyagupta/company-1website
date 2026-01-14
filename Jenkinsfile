pipeline {
    agent any

    stages {

        stage('Stop old container') {
            steps {
                bat 'docker rm -f company1-website || exit 0'
            }
        }

        stage('Checkout Code') {
            steps {
                echo 'Pulling code from Github'
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker Image'
                bat 'docker build -t company1-website .'
            }
        }

        stage('Run docker container') {
            steps {
                echo 'Running Docker container'
                bat 'docker run -d -p 8070:80 --name company1-website company1-website'
            }
        }
    }
}
