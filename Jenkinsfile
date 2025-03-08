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
                bat 'docker build -t jenkin_cicd_nodejs_express_image .'
            }
        }

        stage('Deploy Application') {
            steps {
                bat 'docker stop jenkin_cicd_nodejs_express_container || echo Container not found to stop'
                bat 'docker rm jenkin_cicd_nodejs_express_container || echo Container not found to remove'
                bat 'docker run -d -p 3000:3000 --name jenkin_cicd_nodejs_express_container jenkin_cicd_nodejs_express_image'
            }
        }
    }
}
