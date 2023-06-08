// import groovy.json.JsonOutput


properties(
  [
    parameters([
      booleanParam(defaultValue: false, description: 'if merged', name: '$.pull_request.merged')
    ])
  ]
)

// def result = httpRequest(
//     httpMode: "GET",
//     url: "https://api.github.com/repos/test-user/test-repository/pulls",
//     contentType: "APPLICATION_JSON_UTF8",
//     customHeaders: [[name: "Authorization", value: "token 1a35c322bf25a98dca3d104c5fe0d43b3fbd3c9c"]],
//     consoleLogResponseBody: true,
//     requestBody: JsonOutput.toJson(body),  // JsonOutput은 한글 깨짐 현상이 발생하므로 주의
//     timeout: 5000
// )


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
      def jsonSlurper = new JsonSlurper()
      steps {
          bat 'echo test'
          echo "env:  ${env.getEnvironment()}"
          
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