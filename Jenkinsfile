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
}
    {
        stage ('Test Stage') {

            steps {
                withMaven(maven:'LocalMaven') {
                    sh 'mvn test'
                }
            }

}
}
    {
        stage ('package Stage') {

            steps {
                withMaven(maven:'LocalMaven') {
                    sh 'mvn package'
                }
            }

}
}
      {
        stage ('Install Stage') {

            steps {
                withMaven(maven:'LocalMaven') {
                    sh 'mvn install'
                }
            }
}
}
     {
        stage ('deploy Stage') {
    sshagent (credentials: ['cccdae4b-fe34-4476-ab6d-c5c2d75d4e29']) {
    sh 'scp -o StrictHostKeyChecking=no -l */target/*.war ec2-user@54.196.10.104:/var/lib/tomcat/webapps'
                
            }
        }
}
}

