pipeline {
  agent any
  stages {
    stage('Compile') {
      steps {
        script{
                def mvnHome = tool name: 'MAVEN_HOME', type: 'maven'
                sh "${mvnHome}/bin/mvn package"
        }
      }
    }
    stage('Building Docker Image') {
      steps{
        script {
          sh "docker build -t renubaskar7/cicd-poc-jenkins-ansible:$BUILD_NUMBER ."
        }
      }
    }
    stage('Push Image To Docker Hub') {
      steps{
        script {
          sh "echo $USER"
          sh "docker login -u renubaskar7 -p important5"
          sh "docker push renubaskar7/cicd-poc-jenkins-ansible:$BUILD_NUMBER"
          }
        }
      }
    }
}

