pipeline {
  agent any
  
  tools {nodejs "node"}
  
  environment {
   GITHUB_TOKEN = credentials('csye7125')
  }

  stages {
    stage('Checkout code') {
      steps {
        cleanWs()
        checkout scm
      }
    }
    // stage('Build') {
    //     steps {
    //         cleanWs()
    //         checkout([$class: 'GitSCM', branches: [[name: '*/assignment5']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'gitrepo', url: 'https://github.com/rolwynquadras/helm-chart.git']]])
    //         // sh "ls -lart ./*"
    //     }
    // }
    stage('Create Release') {
      steps {
        //withCredentials([usernamePassword(credentialsId: 'gitrepo', usernameVariable : 'USERNAME', passwordVariable: 'GITTOKEN')])
        
          sh '''
          npm install ci
          ls -al
          GITHUB_TOKEN=$GITTOKEN npx semantic-release
          '''
        
      }
    }
  }
}
