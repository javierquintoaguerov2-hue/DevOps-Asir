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

        stage('Desplegar en VM') {
            steps {
                echo 'Desplegando archivos en la máquina virtual...'

                sh """
                    smbclient //192.168.1.36/C\$ -U "QuintoV2" -c "mkdir Deploy/HTML"
                    smbclient //192.168.1.36/C\$ -U "QuintoV2" -c "put project/index.html Deploy/HTML/index.html"
                """
            }
        }

    }
}
