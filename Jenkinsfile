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
				sh 'docker run app'
				sh 'nc -vz localhost 80'
				sh 'docker stop app'
			}
		}
		stage('Push Registry') {
			steps{
				echo 'Retaggear a stable'
				sh 'docker tag app victorivanserna/app:stable'
				sh 'docker push victorivanserna/app:stable'
			} 
		}
	}
}
