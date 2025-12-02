pipeline {
    agent any

    environment {
        REMOTE_IP = "192.168.1.36"
        REMOTE_SHARE = "\\\\192.168.1.36\\DevOpsHTML"
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/javierquintoaguerov2-hue/DevOps-Asir.git'
            }
        }

        stage('Preparar proyecto') {
            steps {
                echo "Preparando archivos..."
                sh '''
                    mkdir -p project
                    cp index.html project/index.html
                '''
            }
        }

        stage('Validación') {
            steps {
                echo "Validando proyecto..."
            }
        }

        stage('Desplegar en VM') {
            steps {
                echo "Desplegando en la máquina virtual por SMB..."

                withCredentials([usernamePassword(credentialsId: 'smb-credenciales',
                                                 usernameVariable: 'USER',
                                                 passwordVariable: 'PASS')]) {

                    sh '''
                        echo "Montando recurso SMB..."

                        # Montar conexión SMB con usuario y contraseña
                        smbclient //192.168.1.36/DevOpsHTML $PASS -U $USER -c "put project/index.html index.html"

                        echo "Archivo desplegado correctamente en la VM."
                    '''
                }
            }
        }
    }
}

