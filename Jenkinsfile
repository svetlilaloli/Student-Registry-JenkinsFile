pipeline {
	agent any
	environment {
    	REPO = 'svetlilaloli/student-registry-jenkins'
		// IMAGE = '%REPO%:1.0.%BUILD_NUMBER%'
      IMAGE = bat(returnStdout: true, script: '%REPO%:1.0.%BUILD_NUMBER%')
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
        stage('Build Docker image'){
            steps {
              	bat 'docker build -t %IMAGE% .'
            }
        }
        stage('Tag latest'){
          	steps {
            	bat 'docker tag %IMAGE% %REPO%:latest'
          	}
        }
        stage('Push images to DockerHub'){
          	steps {
            	withCredentials([usernamePassword(credentialsId: 'c4cea218-b85f-462c-9098-d10aa6056303', 
                    	passwordVariable: 'password', usernameVariable: 'username')]) {
                	bat 'docker login -u %username% --password %password%'
            	}
            	bat 'docker push %IMAGE%'
            	bat 'docker push %REPO%:latest'
          	}
        }
        stage('Deploy') {
            // when {
            //   branch 'main'
            // }
            steps {
				bat 'docker pull %REPO%:latest'
            	bat 'docker run -d -p 3030:3030 %REPO%:latest'
            }
        }
    }
}