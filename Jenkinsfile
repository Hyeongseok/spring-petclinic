node('TestServer') {
    
  stage('Compile') {
    git url: 'https://github.com/Hyeongseok/spring-petclinic.git'
    def mvnHome = tool 'Maven 3.5.3 Alpine'
    sh "${mvnHome}/bin/mvn -B compile"
  }
  
  stage('Test') {
    git url: 'https://github.com/Hyeongseok/spring-petclinic.git'
    def mvnHome = tool 'Maven 3.5.3 Alpine'
    sh "${mvnHome}/bin/mvn -B verify"
    //step([$class: 'ArtifactArchiver', artifacts: '**/target/*.war', fingerprint: true])    
    step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/TEST-*.xml'])
  }
}
