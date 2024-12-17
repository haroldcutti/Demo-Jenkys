pipeline {
    agent {
        docker {
            image 'node:18' // Imagen base con Node.js
        }
    }
    stages {
        stage('Install Dependencies') {
            steps {
                script {
                    sh 'npm install'
                }
            }
        }
        stage('Build') {
            steps {
                script {
                    sh 'npm run build --prod'
                }
            }
        }
        stage('Dockerize') {
            steps {
                script {
                    sh '''
                    docker build -t demo-jenkys .
                    '''
                }
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                    sh '''
                    docker run -d -p 8080:80 demo-jenkys
                    '''
                }
            }
        }
    }
}
