pipeline {
	agent any
	tools {
		nodejs 'NodeJS'
	}
	environment {
		SONAR_SCANNER_HOME = '/home/hb/Downloads/sonar-scanner-6.2.1.4610-linux-x64'
		SONAR_PROJECT_TOKEN = tool 'SonarQubeScanner'

	}
	stages {
		stage('GitHub'){
			steps {
				git branch: 'main', credentialsId: 'jen-git-dind', url: 'https://github.com/0xhb/CICD01.git'
			}
		}

		stage('Unit Test'){
			steps {
				sh 'npm test'
				sh 'npm install'
			}
		}

		stage('SonarQube Analysis'){
			steps {
				withCredentials([string(credentialsId: 'cicd01-token', variable: 'SONAR_TOKEN')]) {
					withSonarQubeEnv('SonarQube') {
						sh """
						${SONAR_SCANNER_HOME}/bin/sonar-scanner \
						-Dsonar.projectKey=${SONAR_PROJECT_TOKEN} \
						-Dsonar.sources=. \
						-Dsonar.host.url=http://localhost:9000 \
						-Dsonar.login=${SONAR_TOKEN}
						"""
					}
				}
			}
		}
	}
}	