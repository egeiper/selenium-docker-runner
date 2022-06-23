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
	stage('Report') {
    steps {
   
    }
}
}
	post{
		always{
			 script {
            allure([
                    includeProperties: false,
                    jdk: '',
                    properties: [],
                    reportBuildPolicy: 'ALWAYS',
                    results: [[path: 'allure-results']]
            ])
    }
			archiveArtifacts artifacts: 'allure-results/**'
			sh "docker-compose down"
		}
	}
}