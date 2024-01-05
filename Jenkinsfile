pipeline {
	agent any
	stages {
		stage ('Build Backend') {
			steps {
				sh 'mvn clean package -DskipTests=true'
			}
		}
		stage('GitGuardian Scan') {
            		agent {
                		docker { image 'gitguardian/ggshield:latest' }
            		}
            		environment {
                		GITGUARDIAN_API_KEY = credentials('c6b6Bddab27B6DC4d8B974ccfEDe87CbeCee3AbFFd1cCb88A58E3fD4D8C6B54D7DBB45a')
            		}
            		steps {
                		sh 'ggshield secret scan ci'
            		}
		}
	}
}
