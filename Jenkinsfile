pipeline {
    agent any
    triggers {
        pollSCM('* * * * *')
    }
    environment {
        PROYECTO = 'jenkins-labs'
        VERSION  = '1.0'
    }
    stages {
        stage('Info') {
            steps {
                echo "Proyecto: ${PROYECTO}"
                echo "Versión: ${VERSION}"
                echo "Build number: ${BUILD_NUMBER}"
                echo "Job name: ${JOB_NAME}"
            }
        }
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
            echo "Pipeline ${PROYECTO} v${VERSION} completado!"
        }
        failure {
            echo 'Algo falló!'
        }
    }
}