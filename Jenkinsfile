pipeline {
    agent any
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
    }
}
