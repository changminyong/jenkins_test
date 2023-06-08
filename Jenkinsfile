
// properties(
//   [
//     parameters([
//       booleanParam(defaultValue: false, description: 'if merged', name: '$.pull_request.merged')
//     ])
//   ]
// )

// triggers {
//     GenericTrigger(
//      genericVariables: [
//       [key: 'REPO_NAME', value: '$.repository.name', defaultValue: 'null'],
//       [key: 'PR_TYPE', value: '$.pullrequest.type', defaultValue: 'null']
//      ],
//      causeString: 'Triggered By Github',
//      token: '12345678',
//      tokenCredentialId: '',
//      printContributedVariables: true,
//      printPostContent: true,
//      silentResponse: false
//     )
//   }

// // PIPELINE
// pipeline {
//   agent any
//   stages {
//     stage('test') {
//       steps {
//           bat 'echo test'
//           echo "env:  ${env.getEnvironment()}"
          
//       }
//     }
//   //   stage('merged') {
//   //     when {
//   //       expression { params.IF_MERGED == true }
//   //     }
      
//   //     steps {
//   //         bat 'echo merged'
//   //     }
//   //   }
//   }
  
// }

pipeline {
  agent any
  triggers {
    GenericTrigger(
     genericVariables: [
      [key: 'REPO_NAME', value: '$.repository.name', defaultValue: 'null'],
      [key: 'PR_TYPE', value: '$.pullrequest.type', defaultValue: 'null']
     ],
     causeString: 'Triggered By Github',
     token: '12345678',
     tokenCredentialId: '',
     printContributedVariables: true,
     printPostContent: true,
     silentResponse: false
    )
  }
  stages {
    stage('ProcessWebHook') {
      steps {
          script {
            echo "Received a Webhook Request from Guthub."
            echo "RepoName: $REPO_NAME"
            
          }
      }
    }
  }
}