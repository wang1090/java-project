node('linux'){
  stage('UnitTests'){
    git 'https://github.com/wang1090/java-project.git' 
    sh 'ant -f test.xml -v'
    junit 'reports/result.xml'
  }
}
