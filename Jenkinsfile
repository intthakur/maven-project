pipeline {
    agent any


    stages {
        stage('SCM Checkout'){
          git 'https://github.com/prakashk0301/maven-project'
        }
  }
    {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'maven') {
                    sh 'mvn clean compile'
                }
            }
       }
        stage ('Test'){
            steps {
                withMaven (maven: 'maven'){
                  sh 'mvn clean test'
                }
            }
        }
        
        stage ('Install'){
            steps{
                withMaven (maven: 'maven'){
                  sh 'mvn install'
                }
            }
        }
}
}
