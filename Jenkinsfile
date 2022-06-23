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
    script {
            allure([
                    includeProperties: false,
                    jdk: '',
                    properties: [],
                    reportBuildPolicy: 'ALWAYS',
                    results: [[path: 'allure-results']]
            ])
    }
    }
}
}
	post{
		always{
			archiveArtifacts artifacts: 'allure-results/**'
			sh "docker-compose down"
		}
	}
}