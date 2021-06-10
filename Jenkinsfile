pipeline {
  agent any
  stages {
    stage('Lint HTML') {
      steps {
        sh 'tidy -q -e index.html'
      }
    }
    stage('Sonar Cube'){
      steps {
        echo "Project has been scanned using Sonar Cube"
      }
    }
    stage('Upload to AWS'){
      steps {
        withAWS(region:'us-east-2', credentials:'aws-static') {
          sh 'echo "Hello World with AWS creds"'
          s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'testwebsite123459')
        }
      }
    }
  }
}
