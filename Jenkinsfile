pipeline {
	agent any
	environment {
    	REPO = 'svetlilaloli/student-registry-jenkins'
		IMAGE = '%REPO%:1.0.%BUILD_NUMBER%'
  	}
    stages {
        // stage('Install dependencies') {
        //     steps {
        //       bat 'npm install'
        //     }
        // }
        // stage('Security test') {
        //     steps {
        //       bat 'npm audit'
        //     }
        // }
        // stage('Integration test') {
        //     steps {
        //       bat 'npm test'
        //     }
        // }
        stage('Build Docker image'){
            steps {
				bat set
              	// bat 'docker build -t %REPO%:1.0.%BUILD_NUMBER% .'
            }
        }
        // stage('Tag latest'){
        //   	steps {
        //     	bat 'docker tag %REPO%:1.0.%BUILD_NUMBER% %REPO%:latest'
        //   	}
        // }
        // stage('Push images to DockerHub'){
        //   	steps {
        //     	withCredentials([usernamePassword(credentialsId: 'c4cea218-b85f-462c-9098-d10aa6056303', 
        //             	passwordVariable: 'password', usernameVariable: 'username')]) {
        //         	bat 'docker login -u %username% --password %password%'
        //     	}
        //     	bat 'docker push %IMAGE%'
        //     	bat 'docker push %REPO%:latest'
        //   	}
        // }
        // stage('Deploy') {
        //     when {
        //       branch 'main'
        //     }
        //     steps {
        //     	bat 'docker-compose up -d'
        //     }
        // }
    }
}