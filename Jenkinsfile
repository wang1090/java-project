node('linux'){
  stage('UnitTests'){
    git 'https://github.com/wang1090/java-project.git' 
    sh 'ant -f test.xml -v'
    junit 'reports/result.xml'

  }
  stage('Build'){
   sh 'ant -f build.xml -v' 
  }
  stage('Deploy'){
    sh 'aws s3 cp $WORKSPACE/dist/*.jar  s3://seis665assignment10/rectangle-${BUILD_NUMBER}.jar'
  }
  stage('Report'){
    withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'd01f2740-4374-4d54-a850-2ed4bdc8d65b', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
    // some block
       sh 'aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins'
    }
  }
}
