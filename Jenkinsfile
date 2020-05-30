pipeline 
{
    agent any
      stages 
          {
             stage('SCM Checkout')
               {
                 git 'https://github.com/intthakur/maven-project.git'
               }
           }
           {
              stage ('Clean work dirs')
                {
                  
                  steps 
                   {
                     withAnt (installation: 'ant') 
                      {
                        sh 'ant info'
                      }
                    }
                 }
                       
                stage ('package')
                  {
                    steps
                      {
                         withAnt (installation: 'ant')
                          {
                            sh 'ant package'
                          }
                       }
                   }
                stage ('archieve')
                  {
                    steps
                      {
                         withAnt (installation: 'ant')
                          {
                            sh 'ant war'
                          }
                       }
                   }
                
            }
}
