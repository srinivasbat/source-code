pipeline {
  agent {
    label 'jenkins-slave'
  }
  
  stages {
    stage('Clone') {
      steps {
        git branch: 'master', url: 'https://github.com/srinivasbat/source-code.git'
      }
    }
    
    stage('Deploy') {
      steps {
        sh 'cp -r /root/workspace/sourcecode/assets/css/*.css /var/www/html/'
        sh 'cp -r /root/workspace/sourcecode/images/*.png /var/www/html/'
        sh 'cp -r /root/workspace/sourcecode/images/*.jpg /var/www/html/'
        sh 'cp -r /root/workspace/sourcecode/index.html  /var/www/html/'
        sh 'cp -r /root/workspace/sourcecode/assets/fonts/* /var/www/html/fonts/'
        sh 'cp -r /root/workspace/sourcecode/assets/js/*  /var/www/html/js/'
        sh 'cp -r /root/workspace/sourcecode/assets/sass/*  /var/www/html/sass/'
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
