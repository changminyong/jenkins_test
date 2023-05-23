
// PIPELINE
pipeline {
  agent none
  
  stages {
    stage('PRE-PROCESS') {
      agent {
        label 'linux'
      }
      steps {
        script {
            echo "test"
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
                echo "build and test"
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