pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/javierquintoagueroV2-hue/DevOps-Asir.git'
            }
        }

        stage('Preparar proyecto') {
            steps {
                echo 'Preparando archivos...'
                powershell """
                New-Item -ItemType Directory -Force -Path project
                Copy-Item -Path index.html -Destination project -Force
                """
            }
        }

        stage('Desplegar en VM') {
            steps {
                echo 'Desplegando en la máquina virtual...'
                powershell """
                Copy-Item project\\* \\\\192.168.1.36\\C$\\Deploy\\HTML -Recurse -Force
                """
            }
        }
    }
}
