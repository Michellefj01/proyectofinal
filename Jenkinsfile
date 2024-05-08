pipeline {
    agent {
        docker {
            image 'docker:latest'
            args '-v /var/run/docker.sock:/var/run/docker.sock'
        }
    }
    stages {
        stage("Clone Git Repository") {
            steps {
                git(
                    url: "https://github.com/Michellefj01/proyectofinal.git",
                    branch: "main",
                    changelog: true,
                    poll: true
                )
            }   
        }
        stage('Construir imagen de Docker') {
            steps {
                script {
                    // Construye la imagen de Docker
                    sh 'docker build -t proyectofinal:latest .'
                }
            }
        }
    }
}
