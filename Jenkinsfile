pipeline {
    agent any
    triggers {
        pollSCM('* * * * *')  // revisa cada minuto
    }
    stages {
        stage('Clonar código') {
            steps {
                echo 'Clonando repositorio...'
            }
        }
        stage('Verificar') {
            steps {
                echo 'Verificando archivos...'
                sh 'ls -la'
            }
        }
    }
    post {
        success {
            echo 'Pipeline completado exitosamente!'
        }
        failure {
            echo 'Algo falló!'
        }
    }
}
