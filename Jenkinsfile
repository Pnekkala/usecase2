pipeline {
    agent any 
      stages{
        stage('install git'){
            
                sh "echo 'sudo yum install git -y'"
            }
        stage('code commit')
        {
          try {
            sh 'git clone https://github.com/Pnekkala/usecase2.git'
        }
          catch(err) {
            sh "echo 'Error cloning Git bucket'"
        }
        }
        stage('Validate') {
            steps{
                    sh '/usr/local/bin/cfn-lint ./2-tier-Arch.json'
            }
        }
        stage('Dev') {
            steps{   
                    sh"/usr/bin/aws cloudformation create-stack --stack-name test-cicd-2-tier-jenkins-dev --template-body file://2-tier-Arch.json --parameters file://Param-2-tier-Arch.json --region 'us-east-1'"        
         }
    }
}
    }

