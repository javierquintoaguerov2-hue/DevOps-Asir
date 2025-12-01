pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/javierquintoaguerov2-hue/DevOps-Asir.git'
            }
        }

        stage('Preparar proyecto') {
            steps {
                echo 'Preparando archivos...'

                sh """
                    mkdir -p project
                    cp index.html project/index.html
                """
            }
        }

        stage('Validación') {
            steps {
                echo 'Validando proyecto...'
            }
        }

        stage('Simulación de despliegue') {
            steps {
                echo 'Despliegue listo para enviarse a la máquina virtual (WinRM/SMB manual).'
            }
        }

    }
}

