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
        powershell 'docker build -t mateosb/webserver:v1 .'
      }
    }

    stage('Contenedor ') {
      steps {
        powershell(script: 'docker images', returnStatus: true, returnStdout: true)
        powershell 'docker run -d --name WebServerCI -p 80:80 mateosb/webserver:v1'
      }
    }

    stage('Login Docker Hub') {
      steps {
        echo 'Estatus del Contenedor'
        powershell 'docker ps'
      }
    }

    stage('Sube a Docker hub') {
      steps {
        powershell 'docker push mateosb/webserver:v1'
      }
    }

    stage('Mensaje de fin') {
      steps {
        echo 'Crear imagen, ejecutar en contenedor y subir a docker hub'
      }
    }

  }
}