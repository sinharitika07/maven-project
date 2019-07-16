pipeline {
agent any
stages {
stage('SCM Checkout'){
git 'https://github.com/sinharitika07/maven-project.git'
}
}
{
stage ('Compile Stage') {
agent {label 'master'}
steps {
withMaven(maven : 'LocalMaven')
{
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
  
stage('SonarQube analysis') {
            steps {
                withSonarQubeEnv('sonarQube') {
                    // Optionally use a Maven environment you've configured already
                    withMaven(maven : 'LocalMaven') {
                        sh 'mvn clean package sonar:sonar'
                    }
                }
            }
        }

stage ('Deploy Stage') {
steps {

sshagent (credentials: ['7879f3c1-ec02-4f0f-aacd-19dcb445ef5f']) {
sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@3.82.160.158:/var/lib/tomcat/webapps'
}
}
}  

  
}
}
