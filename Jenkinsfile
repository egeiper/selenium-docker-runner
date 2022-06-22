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
	stage ("Stop Grid"){
		steps{
		sh "docker-compose down"
	}
	}
	}
}