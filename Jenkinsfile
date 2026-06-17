pipeline{
	agent any
	tools{
		maven 'Maven'
		}
	environment{
		LANG='en_US.UTF-8'
		LC_ALL='en_US.UTF-8'}
	stages{
		stage('Checkout'){
			steps{  
			git branch: 'master' ,url='https://github.com/fluffy-panda07/MyMavenAnsibleApp.git'}
			}
		stage('Build'){
			steps{ sh 'mvn clean install' }
			}
		stage('Test'){
			steps{ sh 'mvn test' }
			}
		stage('archive'){
			steps{  archiveArtifacts artifacts:'target/*.war',fingerprint:true }
			}
		stage('Deploy'){
			steps{ sh 'ansible-playbook ansible/playbook.yml -i ansible/hosts.ini' }
			}
		}
	post{
		success{ echo 'Build and deployment successfully' }
		failure{ echo 'Build failed' }
		}
	}
	
			
