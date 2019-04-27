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
    sh 'aws s3 cp $WORKSPACE/dist/*.jar  s3://seis6651/rectangle-${BUILD_NUMBER}.jar'
  }
}
