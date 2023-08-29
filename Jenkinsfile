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
  static def UPDATE_CASE = 1
  static def TEST = 2
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
            Global.GIT_COMMIT = bat(script: '@echo off && git rev-parse --short=9 HEAD', returnStdout: true).trim()
            Global.BASE_RESULT_PATH_WIN = "C:\\Jenkins\\sanity_check\\base_results\\core_ffc_main"
            catchError(buildResult: 'UNSTABLE', stageResult: 'FAILURE') {
              bat "exit 1"
            }
            
          }
          echo "test :  ${test}"
          echo "Global.GIT_COMMIT :  ${Global.GIT_COMMIT}"
          echo "Global.BASE_RESULT_PATH_WIN :  ${Global.BASE_RESULT_PATH_WIN}"
          echo "Global.UPDATE_CASE :  ${Global.UPDATE_CASE}"
          echo "env.GIT_COMMIT :  ${env.GIT_COMMIT}"
          echo "env.GIT_PREVIOUS_COMMIT :  ${env.GIT_PREVIOUS_COMMIT}"
          echo "echo ${env.GIT_COMMIT} > ${Global.BASE_RESULT_PATH_WIN}\\commit_id.txt" 

          
      }
    }
    stage('test 2') {
      when {
        expression { 
          Global.UPDATE_CASE == 1 &&
          Global.TEST == 2}
      }
      
      steps {
          bat 'echo UPDATE_CASE'
          // bat(script: 'git rev-parse --short=9 HEAD', returnStdout: true).trim()
          // echo "Global.GIT_COMMIT :  ${Global.GIT_COMMIT}"
      }
    }
    stage('merged') {
      when {
        expression { params.IF_MERGED == true }
      }
      
      steps {
          bat 'echo merged'

          bat "echo new"
          // bat(script: 'git rev-parse --short=9 HEAD', returnStdout: true).trim()
          // echo "Global.GIT_COMMIT :  ${Global.GIT_COMMIT}"
      }
    }
  }
  
}
