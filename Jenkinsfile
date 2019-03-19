node {
   stage('init') {
      checkout scm
   }
   stage('build') {
      sh '''
         mvn clean package
      '''
   }
   stage('deploy') {
      azureWebAppPublish azureCredentialsId: env.AZURE_CRED_ID,
      resourceGroup: env.RES_GROUP, appName: env.WEB_APP, filePath: "**/helloworld2.war"
   }
   archiveArtifacts artifacts: '**/*.war', onlyIfSuccessful: true
}