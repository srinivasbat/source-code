pipeline {
  agent {
    label 'jenkins-slave'
  }

  stages {
    stage('BeforeInstall') {
      steps {
        sh 'chmod +x install_dependencies'
        sh 'chmod +x start_server'
        sh 'chmod +x stop_server'
      }
    }

    stage('Deploy') {
      steps {
        sh './install_dependencies'
        sh './start_server'
        sh 'cp -r assets /var/www/html/'
        sh 'cp -r images /var/www/html/'
        sh 'cp index.html /var/www/html/'
      }
    }

    stage('ApplicationStop') {
      steps {
        sh './stop_server'
      }
    }
  }
}
