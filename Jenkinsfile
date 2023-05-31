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