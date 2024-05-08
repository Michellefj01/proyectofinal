pipeline {
    agent any
    
    environment {
        // Define las credenciales de Kubernetes
        KUBECONFIG = credentials('kubernetes')
        // Define el nombre del namespace en Kubernetes
        NAMESPACE = 'final_namespace'
        // Define el nombre del deployment en Kubernetes
        DEPLOYMENT_NAME = 'final_deployment'
    }
    
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
        
        stage('Desplegar en Kubernetes') {
            steps {
                script {
                    // Despliega la imagen en Kubernetes
                    sh "kubectl --kubeconfig=${KUBECONFIG} --namespace=${NAMESPACE} set image deployment/${DEPLOYMENT_NAME} *=michellefj/proyectofinal:latest"
                }
            }
        }
    }
}
