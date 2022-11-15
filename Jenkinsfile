pipeline {
    agent any
    
    // tools {nodejs "node"}
    
    environment {
        CURRENT_VERSION = currentVersion()
        NEXT_VERSION = nextVersion()
    }

    stages {
        stage('Checkout code') {
            steps {
                checkout scm
            }
        }
        // stage('Build') {
        //     steps {
        //         checkout([$class: 'GitSCM', branches: [[name: '*/assignment5']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'gitrepo', url: 'https://github.com/rolwynquadras/helm-chart.git']]])
        //         // sh "ls -lart ./*"
        //     }
        // }
        stage('Create Semantic Versioning') {
            steps {
                sh '''
                cd ./appdeployment
                ls -al
                sed 's/'${CURRENT_VERSION}'/'${NEXT_VERSION}'/g' ./Chart.yaml
                cat Chart.yaml
                '''
                echo "current vesion = ${CURRENT_VERSION}"
                echo "next version = ${NEXT_VERSION}"
                
            }
        }
    }
    post { 
        always {
            echo 'Post task!'
        }
    }
}