pipeline {
      agent any
      stages {
         stage ('Build') {
          steps {
             sh '''cd $WORKSPACE
                   docker build -t devops-react:v${BUILD_NUMBER} .'''
             }
           }
           stage('push ECR'){
            steps {
                sh '''
		aws ecr get-login-password --region us-west-2 | docker login --username AWS --password-stdin 144486164212.dkr.ecr.us-west-2.amazonaws.com
           		    
		docker tag devops-react:v${BUILD_NUMBER} 144486164212.dkr.ecr.us-west-2.amazonaws.com/talent/reactjs:v${BUILD_NUMBER}
                docker push 144486164212.dkr.ecr.us-west-2.amazonaws.com/talent/reactjs:v${BUILD_NUMBER}   
       '''
            }
          }
          }
        }
