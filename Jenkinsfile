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
}
