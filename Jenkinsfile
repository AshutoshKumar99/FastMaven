node 
{
stage('Project Name')
{
echo 'This is Opstree CI CD'
}

stage('Checkout Code')
{
git 'https://github.com/AshutoshKumar99/FastMaven.git'
}

stage('Build Code')
{

bat 'mvn clean install -Dmaven.test.failure.ignore=true'
}

stage ('JUnit report')
  {
    archive "target/**/*"
    junit 'target/surefire-reports/*.xml' 
  }


  stage('Code coverage')
  {
   archiveArtifacts "target/**/*"

  // publish html
  // snippet generator doesn't include "target:"
  // https://issues.jenkins-ci.org/browse/JENKINS-29711.
  publishHTML (target: [
      allowMissing: false,
      alwaysLinkToLastBuild: false,
      keepAll: true,
      reportDir: 'coverage',
      reportFiles: 'index.html',
      reportName: "RCov Report"
    ])

  }
  
  

}
