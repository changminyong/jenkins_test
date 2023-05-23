
// PIPELINE
pipeline {
  agent none
  
  stages {
    stage('PRE-PROCESS') {
      agent none
      steps {
        script {
            bat 'echo test'
        }
      }
      post {
        always {
          cleanWs notFailBuild: true
        }
      }
    }
    
    stage('Build and Test') {
        steps {
            script {
                bat 'echo test'
            }
        }
        post {
            always {
              cleanWs notFailBuild: true
            }
        }
    }
  }
}