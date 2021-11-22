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
 git branch: 'development', credentialsId: '58154529-75fa-4ae8-8cbb-a2f670fbad9d', url: 'https://github.com/ECE-4th-year-project/maven-web-application.git'
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
  sshagent(['bc4493a2-519c-4926-b84a-da034e922a67']){
  sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@35.154.37.157/:/opt/apache-tomcat-9.0.54/webapps/"
  }
 }
 */
 stage('SendEmailNotification')
 {
 emailext body: '''Build Over - Scriptedway

 Regards,
 Mithun Software Solutions,
 9980923226''', subject: 'Build Over - Scriptedway', to: 'sreeharireddy536@gmail.com'
 }
 
}
