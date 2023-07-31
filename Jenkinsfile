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
  static def BASE_RESULT_PATH_WIN = null
}

// PIPELINE
pipeline {
  environment {
    def test = 2
  }
  agent any
  stages {
    stage('test') {
      steps {
          // bat 'echo test'
          // echo "env:  ${env.getEnvironment()}"
          script{
            test = 1
            Global.GIT_COMMIT = bat(script: 'git rev-parse --short=9 HEAD', returnStdout: true).trim()
            Global.BASE_RESULT_PATH_WIN = "C:\\Jenkins\\sanity_check\\base_results\\core_ffc_main"
            
            bat(script: 'move ${Global.BASE_RESULT_PATH_WIN} ${Global.BASE_RESULT_PATH_WIN}_${Global.GIT_COMMIT}')
          }
          echo "Global.GIT_COMMIT :  ${Global.GIT_COMMIT}"
          echo "test :  ${test}"

          
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
