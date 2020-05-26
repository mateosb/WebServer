pipeline {
  agent any
  stages {
    stage('Directorio') {
      parallel {
        stage('Directorio') {
          steps {
            sh 'ls -la '
          }
        }

        stage('Versiones') {
          steps {
            sh '''docker --version
'''
            sh 'git --version'
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