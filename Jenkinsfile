pipeline {
	agent any
	stages {
		stage('GitHub'){
			steps {
				git branch: 'main', credentialsId: 'jen-git-dind', url: 'https://github.com/0xhb/CICD01.git'
			}
		}
	}
}