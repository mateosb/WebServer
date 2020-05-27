pipeline {
  agent any
  stages {
    stage('Directorio') {
      parallel {
        stage('Directorio') {
          steps {
            bat 'dir'
          }
        }

        stage('Versiones') {
          steps {
            bat 'docker --version'
            bat 'git --version'
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