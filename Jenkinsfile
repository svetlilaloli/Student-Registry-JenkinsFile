pipeline {
	agent any
    stages {
        stage("Setup"){
            steps{
                script {
					env.IMAGE = 'svetlilaloli/student-registry-jenkins'
                    def tag = "${env.IMAGE}:1.0.${BUILD_NUMBER}"
                    env.IMAGE_TAG = tag
                }
            }
        }
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
        stage('Build Docker image'){
            steps {
              	bat 'docker build -t %IMAGE_TAG% .'
            }
        }
        stage('Tag latest'){
          	steps {
            	bat 'docker tag %IMAGE_TAG% %IMAGE%:latest'
          	}
        }
        stage('Push images to DockerHub'){
          	steps {
            	withCredentials([usernamePassword(credentialsId: 'c4cea218-b85f-462c-9098-d10aa6056303', 
                    	passwordVariable: 'password', usernameVariable: 'username')]) {
                	bat 'docker login -u %username% --password %password%'
            	}
            	bat 'docker push %IMAGE_TAG%'
            	bat 'docker push %IMAGE%:latest'
          	}
        }
        stage('Deploy') {
            // when {
            //   branch 'main'
            // }
            steps {
				bat 'docker pull %IMAGE%:latest'
            	bat 'docker run -d -p 3030:3030 --name student-registry-app %IMAGE%:latest'
            }
        }
    }
}