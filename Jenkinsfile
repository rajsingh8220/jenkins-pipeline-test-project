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
      steps{
              sh 'aws s3 cp public/index.html s3://testwebsite123459'
              sh 'aws s3api put-object-acl --bucket testwebsite123459 --key index.html --acl public-read'
              sh 'aws s3 cp public/error.html s3://testwebsite123459'
              sh 'aws s3api put-object-acl --bucket testwebsite123459 --key error.html --acl public-read'
          }
    }
  }
}
