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
        
        stage ('package'){
            steps{
                withMaven (maven: 'maven'){
                  sh 'mvn package'
                }
            }
        }
        stage ('deploy'){
            steps{
                  sshagent (credentials: ['f4e16a40-403d-43c0-a139-e10a08f75938']){
                    sh 'scp -o StrictHostKeyChecking=no */target/webapp/*.war ec2-user@172.31.20.101:/var/lib/tomcat/webapps'
                 }
             }
        }   
}
}
