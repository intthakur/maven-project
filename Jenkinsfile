pipeline
{
agent any
stages
{
    stage('compile source code')
   {   steps {  
           withMaven(jdk: 'localjdk-8', maven: 'localmaven') {
               sh 'mvn compile'
}  }
   } 
    
    stage('build source code')
     {  steps {  
            withMaven(jdk: 'localjdk-8', maven: 'localmaven') {
             sh 'mvn package'
              }
         }
      } 
}
}
