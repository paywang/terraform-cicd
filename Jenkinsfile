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
                terraform init
                echo "terraform apply -auto-approve"
           //     terraform apply -auto-approve -var access_key=${AWS_KEY} -var secret_key=${AWS_SECRET}
           //     git add terraform.tfstate
           //     git -c user.name="Shashwat Tripathi" -c user.email="shashwatXXXX@gmail.com" commit -m "terraform state update from Jenkins"
           //     git push https://${REPO_USER}:${REPO_PASS}@github.com/goforgold/node-app-terraform.git master
             '''
       }
     }
   }
}

