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
				
			  
			   bat 'C:\\Windows\\System32\\WindowsPowerShell\\v1.0\\powershell.exe -Command "Invoke-WebRequest -Uri http://localhost:8181/manager/text/deploy?path=/ -Method PUT -InFile C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\build-n-deploy\\target\\\devOpsWeb.war.war"'

			}
		}		
	}
}
