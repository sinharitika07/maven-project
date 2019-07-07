pipeline {
agent any
stages {
stage('SCM Checkout'){
git 'https://github.com/sinharitika07/maven-project.git'
}
}
{
stage ('Compile Stage') {
steps {
withMaven(maven : 'LocalMaven') {
sh 'mvn clean compile'
}
}
}

stage ('Test Stage') {
steps {
withMaven(maven : 'LocalMaven') {
sh 'mvn test'
}
}
}
  
stage ('Install Stage') {
steps {
withMaven(maven : 'LocalMaven') {
sh 'mvn clean install'
}
}
}

stage ('Deploy Stage') {
steps {

sshagent (credentials: ['cccdae4b-fe34-4476-ab6d-c5c2d75d4e29']) {
sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.87.227:/var/lib/tomcat/webapps'
}
}
}  

  
}
}
