pipeline {
  agent any

   options {
  	timeout(time: 1, unit: 'HOURS')
  	disableConcurrentBuilds()
  	buildDiscarder(logRotator(numToKeepStr: '10'))
  	timestamps()
  }

  environment {
    env.PATH += ":/opt/terraform_0.7.13/"
  }
  triggers {
	pollSCM('*/3 * * * *')
  }
  stages {
    stage ('Terraform Plan') {
        sh 'terraform plan -no-color -out=create.tfplan'
    }

    // Optional wait for approval
    input 'Deploy stack?'

    stage ('Terraform Apply') {
        sh 'terraform apply -no-color create.tfplan'
    }

    stage ('Post Run Tests') {
        echo "Insert your infrastructure test of choice and/or application validation here."
        sleep 2
        sh 'terraform show'
  }
 }
}

