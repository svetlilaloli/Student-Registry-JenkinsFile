// Checking out the code
// Setting up Node.js
// Installing dependencies
// Starting the application 
// Running tests

pipeline {
    agent any

    stages {
        stage('Checkout GitHub repo') {
          steps {
            git branch: 'main',
            url: 'https://github.com/svetlilaloli/Student-Registry-JenkinsFile.git'
          }
        }
        stage('Build') {
            steps {
                batchFile('npm install')
            }
        }
        stage('Test') {
            steps {
                batchFile('npm audit')
                batchFile('npm test')
            }
        }
        stage('Deploy') {
            steps {
                // echo 'Deploying....'
            }
        }
    }
}