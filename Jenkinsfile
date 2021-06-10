pipeline {
  agent any
  stages {
    stage('Lint HTML') {
      steps {
        sh 'tidy -q -e index.html'
      }
    }
    stage('Upload to AWS'){
      step {
        withAWS(region:'us-east-2', credentials:'aws-static') {
          sh 'echo "Hello World with AWS creds"'
          s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'adeza-static-jenkins-pipeline')
        }
      }
    }
  }
}
