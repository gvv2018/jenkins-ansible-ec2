properties([disableConcurrentBuilds()])

pipeline {
  agent {
    label 'master'
  }
  options {
    buildDiscarder(logRotator(numToKeepStr: '10'))
    timestamps()
  }

//  triggers {
//    pollSCM('* * * * *')
//  }

  environment{
    AWS_ACCESS_KEY_ID = credentials('AWS_ACCESS_KEY_ID')
    AWS_SECRET_ACCESS_KEY = credentials('AWS_SECRET_ACCESS_KEY')
  }

  stages {
    stage ("Create AWS EC2 Instance") {
      steps {
        sh 'ls'
//        ansiblePlaybook(playbook: 'create-ec2-instance.yml')
      }
    }
    stage ("Install Docker") {
      steps {
        sh 'ansible-playbook --key-file=/home/ubuntu/gvv2012.pem -u ubuntu -i inventory/ec2.py install-app.yml'
      }
    }
  }

}
