pipeline {
	agent any
	stages{
		stage('Build') {
			steps{
				sh 'docker build -t app:test .'
				echo 'BUILD'
			}
		}
		stage('Test') {
			steps{
				echo 'TEST'
				sh 'docker run --rm --name app -id -p 80:80 app:test'
				sh '/bin/nc -vz localhost 80'
			}
			post{
				always {
					sh 'docker container stop app'
				}
			}
		}
		stage('Push Registry') {
			steps{
				echo 'Retaggear a stable'
				sh 'docker tag app:test victorivanserna/app:stable'
				sh 'docker push victorivanserna/app:stable'
			} 
		}
	}
}
