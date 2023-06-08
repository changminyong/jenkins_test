properties(
  [
    parameters([
      booleanParam(defaultValue: false, description: 'if merged', name: '$.pull_request.merged')
    ])
  ]
)

// PIPELINE
pipeline {
  agent any
  triggers {
    GenericTrigger(
      genericVariables:[
        [key: 'merged', value: '$.pull_request.merged']
      ],
      causeString: 'Triggerd on $ref',
      token: 'test',
      tokenCredentialId: '',
      printContributedVariables: true,
      printPostContent: true,
      silentResponse: false,
      regexpFilterText: '$ref',
      regexpFilterExpression: 'refs/heads/' + BRANCH_NAME

    )
  }
  stages {
    stage('test') {
      steps {
          bat 'echo test'
      }
    }
  //   stage('merged') {
  //     when {
  //       expression { params.IF_MERGED == true }
  //     }
      
  //     steps {
  //         bat 'echo merged'
  //     }
  //   }
  }
  
}