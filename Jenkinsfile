pipeline {
    agent any
    
    environment {
        // Utiliza la credencial de Kubernetes configurada en Jenkins
        KUBECONFIG_CRED = credentials('kubernetes')
        NAMESPACE = 'final_namespace'
        DEPLOYMENT_NAME = 'final_deployment'
    }
    
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
                    docker.build('michellefj/proyectofinal:latest')
                }
            }
        }
        
        stage('Desplegar en Kubernetes') {
            steps {
                script {
                    // Utiliza las credenciales de Kubernetes configuradas en Jenkins
                    withCredentials([kubeconfigFile(credentialsId: 'kubernetes', variable: 'KUBECONFIG')]) {
                        sh "kubectl --kubeconfig=${KUBECONFIG} --namespace=${NAMESPACE} set image deployment/${DEPLOYMENT_NAME} *=michellefj/proyectofinal:latest"
                    }
                }
            }
        }
    }
}
