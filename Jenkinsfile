pipeline {
	agent any
	stages{
		stage('Build') {
			steps{
				sh 'whoami'
				sh 'cat /etc/passwd | cut -d":" -f1'
				sh 'docker build -t app .'
			}
		}
		stage('Test') {
			steps{
				echo 'TEST'
			}
		}
		stage('Deploy') {
			steps{
				echo 'DEPLOY'
			} 
		}
	}
}
