pipeline {
  agent any
  stages {
    stage('Directorio') {
      parallel {
        stage('Directorio') {
          steps {
            powershell 'ls'
          }
        }

        stage('Versiones') {
          steps {
            powershell 'docker --version'
            powershell 'git --version'
          }
        }

        stage('Mensaje versiones') {
          steps {
            echo '"Fin de versiones"'
          }
        }

      }
    }

    stage('Inicio') {
      steps {
        echo '"Inicio de CI"'
      }
    }

    stage('Imagen') {
      steps {
        echo 'Creando imagen'
        powershell(script: 'docker build -t mateosb/webserver:v4 .', returnStatus: true, returnStdout: true)
      }
    }

    stage('Contenedor ') {
      steps {
        powershell(script: 'docker images', returnStatus: true, returnStdout: true)
        powershell(script: 'docker run -d --name WebServerCI -p 80:80 mateosb/webserver:v4', returnStatus: true, returnStdout: true)
      }
    }

    stage('Estatus') {
      parallel {
        stage('Estatus') {
          steps {
            echo 'Estatus del Contenedor'
            powershell(script: 'docker ps', returnStatus: true, returnStdout: true)
          }
        }

        stage('Cierre de etapa') {
          steps {
            echo 'Contenedor ejecutandose'
          }
        }

      }
    }

  }
}