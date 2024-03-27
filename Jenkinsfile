pipeline {
	agent any 
	tools {
		maven 'local_maven'	
	}
		
	stages {
		stage ('Build') {
			steps {
				bat 'mvn clean package'
			}
	
			post {
				success {
					echo "Archiving the Artifacts"
					archiveArtifacts artifacts: '**/target/*.war'
				}
			}
		}
		stage ('Deploy to tomcat server'){
			steps {
				
				bat 'Invoke-WebRequest -Uri http://localhost:8181/manager/text/deploy?path=/ -Method PUT -InFile **/*.war'
			}
		}		
	}
}
