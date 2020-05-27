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

    stage('error') {
      steps {
        echo '"Solo imprime las versiones"'
      }
    }

  }
}