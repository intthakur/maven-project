pipeline
{
agent any
stages
{
    stage('compile source code')
   {   steps {  
           withMaven(jdk: 'localjava', maven: 'localmaven') {
               sh 'mvn compile'
}  }
   } 
    
    stage('build source code')
     {  steps {  
            withMaven(jdk: 'localjava-8', maven: 'localmaven') {
             sh 'mvn package'
              }
         }
      } 
}
}
