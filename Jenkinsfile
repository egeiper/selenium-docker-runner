pipeline{
agent any
	stages{
	stage ("Start Grid"){
		steps{
		sh "docker-compose up -d hub firefox"
	}
	}
	stage ("Run Test"){
		steps{
			sh "docker compose up login navigate"
		}
	}
	post{
		always{
			archiveArtifacts artifacts: 'outputDocker/**'
			sh "docker-compose down"
		}
	}
	}
}