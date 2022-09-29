pipeline {
    agent any
    environment{
        DOCKER_TAG = "${BUILD_NUMBER}"
    }
 stages{
        stage('Build Docker Image'){
            steps{
                sh 'docker build -t poretrithynea/vueminiproject:${DOCKER_TAG} .'
            }
        }
        stage('DockerHub Push'){
            steps{
                withCredentials([usernamePassword(credentialsId: 'rithyneahub', usernameVariable: 'dockerUser', passwordVariable: 'dockerHubPwd')]) {
                    sh 'docker login -u ${dockerUser} -p ${dockerHubPwd}'
                    sh 'docker push poretrithynea/vueminiproject:${DOCKER_TAG}'
                }
            }
        }
      }
    }
