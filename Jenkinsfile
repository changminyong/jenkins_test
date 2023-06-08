
properties(
  [
    parameters([
      booleanParam(defaultValue: false, description: 'if merged', name: 'IF_MERGED')
    ])
  ]
)

// PIPELINE
pipeline {
  agent any
  stages {
    stage('test') {
      steps {
          bat 'echo test'
          echo "env:  ${env.getEnvironment()}"
          
      }
    }
    stage('merged') {
      when {
        expression { params.IF_MERGED == true }
      }
      
      steps {
          bat 'echo merged'
      }
    }
  }
  
}
