pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'stage : Build'
      }
    }

    stage('test') {
      parallel {
        stage('unitaire') {
          steps {
            bat(script: 'php bin/phpunit', returnStatus: true, label: 'test')
          }
        }

        stage('intégration') {
          steps {
            bat 'php bin/phpunit'
          }
        }

        stage('fonctionnel') {
          steps {
            bat 'php bin/phpunit'
          }
        }

      }
    }

    stage('deploy') {
      steps {
        powershell 'symfony server:start'
      }
    }

  }
}