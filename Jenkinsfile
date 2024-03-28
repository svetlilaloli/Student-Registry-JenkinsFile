pipeline {
    agent any
    environment {
        REPO = 'svetlilaloli/student-registry-jenkins'
        BUILD_NUMBER = '${env.BUILD_NUMBER}'
        IMAGE = '${REPO}:1.0.${BUILD_NUMBER}'
    }
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
        stage('Deploy') {
          when {
            branch 'main'
          }
        steps {
            bat 'docker build -t %IMAGE% .'
            withCredentials([usernamePassword(credentialsId: 'c4cea218-b85f-462c-9098-d10aa6056303', 
                passwordVariable: 'password', usernameVariable: 'username')]) {
            bat 'docker login -u %username% --password %password%'
            bat 'docker tag %IMAGE% %REPO%:latest'
            bat 'docker push %IMAGE%'
            bat 'docker push %REPO%:latest'
            bat 'docker-compose up -d'
          }
        }
      }
    }
}