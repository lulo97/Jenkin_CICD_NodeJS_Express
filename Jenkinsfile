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
                sh 'npm install'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t Jenkin_CICD_NodeJS_Express_Image .'
            }
        }

        stage('Deploy Application') {
            steps {
                sh 'docker stop Jenkin_CICD_NodeJS_Express_Container || true'
                sh 'docker rm Jenkin_CICD_NodeJS_Express_Container || true'
                sh 'docker run -d -p 3000:3000 --name Jenkin_CICD_NodeJS_Express_Container Jenkin_CICD_NodeJS_Express_Image'
            }
        }
    }
}
