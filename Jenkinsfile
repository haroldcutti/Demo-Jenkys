pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Clonar el repositorio desde GitHub, especificando la rama 'main'
                git url: 'https://github.com/haroldcutti/Demo-Jenkys.git', branch: 'main'
            }
        }
        stage('Install Dependencies') {
            steps {
                script {
                    // Instalar dependencias de Node.js
                    sh 'npm install'
                }
            }
        }
        stage('Build') {
            steps {
                script {
                    // Compilar el proyecto (en este caso, el frontend)
                    sh 'npm run build --prod'
                }
            }
        }
        stage('Dockerize') {
            steps {
                script {
                    // Crear la imagen Docker
                    sh '''
                    docker build -t demo-jenkins .
                    '''
                }
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                    // Ejecutar el contenedor Docker
                    sh '''
                    docker run -d -p 8080:80 demo-jenkins
                    '''
                }
            }
        }
    }
}
