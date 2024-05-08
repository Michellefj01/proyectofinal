pipeline {
    agent any
    
    stages {
        stage('Clonar repositorio') {
            steps {
                git branch: 'main', url: 'https://github.com/Michellefj01/proyectofinal.git'
            }
        }
        
        stage('Construir imagen de Docker') {
            steps {
                script {
                    sh 'pwd'
                    // Construir la imagen de Docker
                    docker.build('michellefj/proyectofinal:latest')
                }
            }
        }
    }
}
