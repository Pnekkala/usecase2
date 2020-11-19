pipeline {


agent any


stages {


stage('Clone') {


steps {


sh 'git clone https://github.com/Pnekkala/usecase2.git'

}


}


stage('Test') {


steps {


sh '/usr/local/bin/cfn-lint ./*.json'


}


}


stage('s3upload') {


steps {


sh '/usr/local/bin/aws s3 cp simples3bucket.json s3://aws-logs-786678469955-ap-southeast-2/simples3bucket.json'


}


}


stage('Deploy') {


steps {


sh 'cd /usr/local/bin/'


sh 'ls'


sh "/usr/local/bin/aws cloudformation create-stack --stack-name s3bucket --template-body file://simples3bucket.json --region 'ap-southeast-2'"


}


}


}


}
