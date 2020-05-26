pipeline {
  agent any
  stages {
    stage('Directorio') {
      parallel {
        stage('Directorio') {
          steps {
            sh 'powershell "Dir" '
          }
        }

        stage('Versiones') {
          steps {
            sh '''powershell "docker --version"
'''
            sh 'powershell "git --version"'
          }
        }

        stage('Mensaje versiones') {
          steps {
            echo '"Fin de versiones"'
          }
        }

      }
    }

    stage('') {
      steps {
        echo '"Solo imprime las versiones"'
      }
    }

  }
}