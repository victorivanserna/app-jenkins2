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
				sh 'docker run -d --name app -p 80:80 app:test'
				sh 'nc -vz localhost 80'
				sh 'docker stop app'
			}
		}
		stage('Push Registry') {
			steps{
				echo 'Retaggear la imagen que tenemos como test a stable'
				withCredentials([usernamePassword(credentialsId: '58b34614-9dd6-4a0c-821d-74e5bedc47fa', passwordVariable: 'password', usernameVariable: 'user')]) {
					sh 'docker tag app:test victorivanserna/app:stable'
					sh 'docker push victorivanserna/app:stable'
				}
				
			} 
		}
	}
}
