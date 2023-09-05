pipeline {
    agent any

    environment {
        DIRECTORY_PATH = "C:/ProgramData/Jenkins/.jenkins/workspace/Task5Pipeline"
        TESTING_ENVIRONMENT = "DeakinTesting"
        PRODUCTION_ENVIRONMENT = "TanyaGujral"
    }

    stages {
        stage('Build') {
            steps {
                echo "In Build stage"
                echo "Fetch the source code from the directory path specified by the path: : ${env.DIRECTORY_PATH}"
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo "In Unit and Integration Test Stage"
                echo "Unit tests done"
                echo "Integration tests done"
            }
			post{
				success{
					mail to: "tanyagujral07@gmail.com",
					subject: "Test Status Email",
					body: "Unit and Integration Tests were successful"
				}
			}
        }

        stage('Code Analysis') {
            steps {
                echo "In Code Analysis Stage"
                echo "Analyze the quality of the code"
            }
        }

        stage('Security Scan') {
            steps {
                echo "In Security Scan Stage"
                echo "Identify security vulnerabilities in code"
            }
			post{
				success{
					mail to: "tanyagujral07@gmail.com",
					subject: "Security Scan Status Email",
					body: "Security Scan was successful"
				}
        }

        stage('Integration Tests on Staging') {
            steps {
                echo "In the stage - 'Integration Tests on Staging'"
                echo "Integration Tests on near-production environment"
            }
        }

        stage('Deploy to Production') {
            steps {
                echo "In Deploy to Production Stage"
                echo "Deploy the application to the ${env.TESTING_ENVIRONMENT} environment"
            }
        }

        stage('Approval') {
            steps {
                script {
                    echo "In Approval Stage"
                    echo "Paused 10 seconds before continuing"
                    sleep(time: 10, unit: 'SECONDS')
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                echo "In Deploy to Production Stage"
                echo "Deploy the code to the ${env.PRODUCTION_ENVIRONMENT} environment"
            }
        }
    }
}
