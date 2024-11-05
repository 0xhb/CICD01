pipeline {
	stages {
		stage('GitHub'){
			steps {
				git branch: 'main', credentialsId: 'jen-git-dind', url: 'https://github.com/0xhb/Complete_CICD_02.git'
			}
		}
	}
}