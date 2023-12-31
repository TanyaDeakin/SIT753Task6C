pipeline {
    agent any

    environment {
        DIRECTORY_PATH = "C:/ProgramData/Jenkins/.jenkins/workspace/Task6CPipeline"
        TESTING_ENVIRONMENT = "DeakinTesting"
        PRODUCTION_ENVIRONMENT = "TanyaGujral"
    }

    stages {
        stage('Build') {
            steps {
                echo "In Build stage"
                echo "Fetch the source code from the directory path specified by the path: ${env.DIRECTORY_PATH}"
		echo "Options of tools for this stage - Gradle, Ant, Maven"
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo "In Unit and Integration Test Stage"
                echo "Unit tests completed"
                echo "Integration tests done"
		echo "Options of tools for this stage - JUnit, TestNG, Selenium"
            }
			post{
				success{
					emailext attachLog: true,
					to: "tanyagujral07@gmail.com",
					subject: "Test Status Email",
					body: "Unit and Integration Tests were successful"
				}
				failure{
					emailext attachLog: true,
					to: "tanyagujral07@gmail.com",
					subject: "Test Status Email",
					body: "Unit and Integration Tests stage failed"
				}
			}
        }

        stage('Code Analysis') {
            steps {
                echo "In Code Analysis Stage"
                echo "Analyze the quality of the code"
		echo "Options of tools for this stage - Sonarqube, Checkmarx, PMD"
            }
        }

        stage('Security Scan') {
            steps {
                echo "In Security Scan Stage"
                echo "Identify security vulnerabilities in code"
		echo "Options of tools for this stage - OWASP ZAP, Nessus, Veracode"
            }
			post{
				success{
					emailext attachLog: true,
					to: "tanyagujral07@gmail.com",
					subject: "Security Scan Status Email",
					body: "Security Scan was successful"
				}
				failure{
					emailext attachLog: true,
					to: "tanyagujral07@gmail.com",
					subject: "Security Scan Status Email",
					body: "Security Scan failed"
				}
			}
        }

        stage('Integration Tests on Staging') {
            steps {
                echo "In the stage - 'Integration Tests on Staging'"
                echo "Integration Tests on near-production environment"
		echo "Options of tools for this stage - AWS Code Deploy, Docker, Kubernetes"
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
