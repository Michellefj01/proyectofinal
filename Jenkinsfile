pipeline {
    agent any
    
    stages {
        stage('Clonar repositorio') {
            steps {
                git branch: 'main', url: 'https://github.com/Michellefj01/proyectofinal.git'
            }
        }
        
        stage('Esperar aprobación') {
            steps {
                // Solicitar aprobación manual antes de continuar
                input '¿Estás seguro de que deseas construir la imagen de Docker?'
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

