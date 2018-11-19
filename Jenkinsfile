pipeline {
 agent any
    stages{
    stage('Build'){
            steps {
                bat 'mvn clean package'
            }
            post {
                success{
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        } 
         stage('Deploy to tomcat staging'){
             steps{
                 build job: 'Deploy war to tomcat'
                              }
         }
         stage ('Deploy to Production'){
            steps{
                
                   build job: 'deploy war to prod'
            }
            post {
                success {
                    echo 'Code deployed to Production.'
                }

                failure {
                    echo ' Deployment failed.'
                }
            }
        }
    }

}