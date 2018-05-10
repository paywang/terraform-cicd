pipeline {
  agent any

   options {
  	timeout(time: 1, unit: 'HOURS')
  	disableConcurrentBuilds()
  	buildDiscarder(logRotator(numToKeepStr: '10'))
  	timestamps()
  }

  triggers {
	pollSCM('*/3 * * * *')
  }
   stages {
     stage('AWS Deployment') {
       steps {
//            sh 'rm -rf node-app-terraform'
//             sh 'git clone https://github.com/goforgold/node-app-terraform.git'
             sh '''
                pwd
                cd ec2
                /usr/local/bin/terraform init
                echo "/usr/local/bin/terraform apply -auto-approve"
                /usr/local/bin/terraform apply -auto-approve

             '''
       }
     }
   }
}

