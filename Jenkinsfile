import jenkins.model.Jenkins

properties(
  [
    parameters([
      booleanParam(defaultValue: false, description: 'if merged', name: 'MERGED')
    ])
  ]
)


// GLOBALS
class Global {
  static def GIT_COMMIT = null
}

// PIPELINE
pipeline {
  agent any
  stages {
    stage('test') {
      steps {
          // bat 'echo test'
          // echo "env:  ${env.getEnvironment()}"
          Global.GIT_COMMIT = bat(script: 'git rev-parse --short=9 HEAD', returnStdout: true)
          echo "Global.GIT_COMMIT :  ${Global.GIT_COMMIT}"
          
      }
    }
    stage('merged') {
      when {
        expression { params.IF_MERGED == true }
      }
      
      steps {
          bat 'echo merged'
          // bat(script: 'git rev-parse --short=9 HEAD', returnStdout: true).trim()
          // echo "Global.GIT_COMMIT :  ${Global.GIT_COMMIT}"
      }
    }
  }
  
}
