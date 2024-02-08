pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'echo "Hi Jenkins team 1! how are you !"'
        sh '''
        echo "Multiline shell steps works too"
        ls - lah 
        '''
      }
    }
    stage('Upload to AWS') {
      steps {
        withAWS(region: 'us-east-1', credentials: 'jenkins-team1') {
        sh 'echo "Uploading content with AWS creds"'
          s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file: 'index.html',
            bucket: 'jenkins-team1')

        }
      }
    }
  }
}
