pipeline {
  agent {
    label 'jenkins-slave'
  }
  
  stages {
    stage('Deploy') {
      steps {
        //sh 'unzip html5up-dimension.zip -d /var/www/html/'
      }
    }
    
    stage('BeforeInstall') {
      steps {
        sh 'chmod +x install_dependencies'
        sh 'chmod +x start_server'
        sh 'chmod +x stop_server'
        
        sh './install_dependencies'
        sh './start_server'
      }
    }
    
    stage('ApplicationStop') {
      steps {
        sh './stop_server'
      }
    }
  }
}
