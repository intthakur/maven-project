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
                 stage ('deploy')
                   {
                      steps
                        {
                           sshagent (credentials: ['f4e16a40-403d-43c0-a139-e10a08f75938'])
                            {
                              sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.31.77:/var/lib/tomcat/webapps'
                            }
                         }
                    }   
            }
}
