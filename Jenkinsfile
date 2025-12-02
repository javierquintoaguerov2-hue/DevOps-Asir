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
                echo "Preparando archivos..."
                sh '''
                    rm -rf project
                    mkdir project
                    cp index.html project/index.html
                '''
            }
        }

        stage('Desplegar en VM (SMB)') {
            steps {
                echo "Desplegando archivo en la máquina virtual con SMB..."

                sh '''
                    smbclient //192.168.1.36/DevOpsHTML \
                        -U Quinto%9899Jq \
                        -c "put project/index.html index.html"
                '''
            }
        }
    }

    post {
        success {
            echo "✔ Despliegue completado correctamente."
        }
        failure {
            echo "❌ Error durante el despliegue."
        }
    }
}


