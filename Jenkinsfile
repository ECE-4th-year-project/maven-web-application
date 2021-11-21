node
{
 def mavenHome = tool name: "maven3.6.3"
 
 //echo "GitHub BranhName ${env.BRANCH_NAME}"
  //echo "Jenkins Job Number is: -->  ${env.BUILD_NUMBER}"
  echo "Jenkins Node Name is: --> ${env.NODE_NAME}"
  
  echo "Jenkins Home is: --> ${env.JENKINS_HOME}"
  echo "Jenkins URL is: -->  ${env.JENKINS_URL}"
  echo "JOB Name is: -->  ${env.JOB_NAME}"
  
  properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '3', daysToKeepStr: '', numToKeepStr: '3')), pipelineTriggers([pollSCM('* * * * * ')])])
  
 stage('CheckoutCode')
 {
  git branch: 'development', credentialsId: '05d44367-ae8e-4ef8-88f3-330b9e349310', url: 'https://github.com/MithunTechnologiesDevOps/maven-web-application.git'
 }

 stage('Build')
 {
 sh "${mavenHome}/bin/mvn clean package"
 }
 /*
 stage('ExecuteSonarQubeReport')
 {
 sh "${mavenHome}/bin/mvn sonar:sonar"
 }
 
 stage('UploadArtifactintoNexus')
 {
 sh "${mavenHome}/bin/mvn deploy"
 }
 
 stage('DeployAppIntoTomcatServer')
 {
  sshagent(['80459334-5776-471c-90c6-277f3fbdd727']) {
  sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@3.25.69.97:/opt/apache-tomcat-9.0.44/webapps/"
  }
 }
 */
 stage('SendEmailNotification')
 {
 emailext body: '''Build Over - Scriptedway

 Regards,
 Mithun Software Solutions,
 9980923226''', subject: 'Build Over - Scriptedway', to: 'devopstrainingblr@gmail.com'
 }
 
}
