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
                withMaven(maven:'LocalMaven') {
                    sh 'mvn clean compile'
                }
            }
        }
                
      {
        stage ('packages Stage') {

            steps {
                withMaven(maven:'LocalMaven') {
                    sh 'mvn package'
                }          
            }
        }
}
}
}
