pipeline {
    agent any
    triggers {
        pollSCM('* * * * *')
    }
    parameters {
        choice(
            name: 'ENTORNO',
            choices: ['desarrollo', 'staging', 'produccion'],
            description: '¿En qué entorno deseas desplegar?'
        )
        booleanParam(
            name: 'EJECUTAR_TESTS',
            defaultValue: true,
            description: '¿Ejecutar pruebas antes de desplegar?'
        )
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
                echo "Entorno seleccionado: ${params.ENTORNO}"
                echo "Build number: ${BUILD_NUMBER}"
            }
        }
        stage('Tests') {
            when {
                expression { params.EJECUTAR_TESTS == true }
            }
            steps {
                echo 'Ejecutando tests...'
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
            echo "Pipeline ${PROYECTO} v${VERSION} desplegado en ${params.ENTORNO}!"
        }
        failure {
            echo 'Algo falló!'
        }
    }
}