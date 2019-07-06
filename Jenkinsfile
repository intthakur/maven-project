 pipeline {
     agent any
     stages {
       stage ('Clone my code') {
         git 'https://github.com/intthakur/maven-project.git'
       }
       stage ('compile my code') {
         steps {
           withMaven (maven : 'LocalMaven') {
             sh 'mvn compile'
           }
         }
       }
       }
}
