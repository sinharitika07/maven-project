 pipeline {
      agent any
      stages {
         stage('clone my code'){
            git 'https://github.com/prakashk0301/maven-project.git'
              }
      }
  {
         stage('compile my code'){
            steps {
               withMaven(maven : 'Maven3.5.2'){
                 sh 'mvn compile'
                   } 
                  }
                  }  
                }
               }
              
