pipeline {
    agent any

    environment {
        NODE_VERSION = '18'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/lulo97/Jenkin_CICD_NodeJS_Express.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t Jenkin_CICD_NodeJS_Express_Image .'
            }
        }

        stage('Deploy Application') {
            steps {
                bat 'docker stop Jenkin_CICD_NodeJS_Express_Container || true'
                bat 'docker rm Jenkin_CICD_NodeJS_Express_Container || true'
                bat 'docker run -d -p 3000:3000 --name Jenkin_CICD_NodeJS_Express_Container Jenkin_CICD_NodeJS_Express_Image'
            }
        }
    }
}
