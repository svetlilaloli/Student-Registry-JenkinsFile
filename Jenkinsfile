pipeline {
    agent any
    // environment {
    //     BUILD_NUMBER = ''
    // }
    stages {
        stage('Install dependencies') {
      steps {
        bat 'npm install'
      }
        }
        stage('Security test') {
      steps {
        bat 'npm audit'
      }
        }
        stage('Integration test') {
      steps {
        bat 'npm test'
      }
        }
      //   stage('Deploy') {
      //     when {
      //       branch 'main'
      //     }
      //   steps {
      //     bat 'docker build -t svetlilaloli/student-registry-jenkins:1.0.%BUILD_NUMBER% .'
      //     withCredentials([usernamePassword(credentialsId: 'c4cea218-b85f-462c-9098-d10aa6056303', 
      //       passwordVariable: 'password', usernameVariable: 'username')]) {
      //       bat 'docker login -u %username% --password %password%'
      //       bat 'docker tag svetlilaloli/student-registry-jenkins:1.0.%BUILD_NUMBER% svetlilaloli/student-registry-jenkins:latest'
      //       bat 'docker push svetlilaloli/student-registry-jenkins:1.0.%BUILD_NUMBER%'
      //       bat 'docker push svetlilaloli/student-registry-jenkins:latest'
      //       bat 'docker pull svetlilaloli/student-registry-jenkins'
      //       bat 'docker-compose up -d'
      //     }
      //   }
      // }
    }
}