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
                 stage ('deploy')
                   {
                      steps
                        {
                           sshagent (credentials: ['6045d0a1-2a4f-44be-b81c-0841697edd66'])
                            {
                              sh 'scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/pipeline-ant/webapp1.war ec2-user@172.31.31.77:/var/lib/tomcat/webapps'
                            }
                         }
                    }   
            }
}
