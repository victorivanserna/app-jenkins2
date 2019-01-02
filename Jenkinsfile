pipeline {
	agent any
	stages{
		stage('Build') {
			steps{
				sh 'docker build -t app .'
				echo 'BUILD'
			}
		}
		stage('Test') {
			steps{
				echo 'TEST'
				sh '/bin/nc -vz localhost 22'
			}
		}
		stage('Push Registry') {
			steps{
				echo 'Retaggear a stable'
				sh 'docker tag app:test app:stable'
				sh 'docker push app:test app:stable'
			} 
		}
	}
}
