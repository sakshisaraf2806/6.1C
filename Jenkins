pipeline {
    agent any

    environment {
        EMAIL = 'sakshidsaraf@gmail.com'
        GITHUB_REPO = 'https://github.com/sakshisaraf2806/6.1C.git'
    }

    stages {
        stage('Build') {
            steps {
		echo “Fetching code from : ${GITHUB_REPO}"
                echo "Stage 1: Build - Using Maven as the build automation tool to compile and package the code."
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo "Stage 2: Unit and Integration Tests - Utilizing JUnit for unit testing and Selenium for integration testing to ensure that all components work together as expected."
            }
            post {
                always {
			emailext(
				subject : “Status of Test Stage : ${currentBuild.result}”,
				body : “This test stage has been completed : ${currentBuild.result}”,
				attachLog : true,
				to : “${EMAIL}"
			)

                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo "Stage 3: Code Analysis - SonarQube is integrated to analyze the code for maintaining high code quality standards."
            }
        }

        stage('Security Scan') {
            steps {
                echo "Stage 4: Security Scan - OWASP ZAP is used to identify any potential security vulnerabilities in the code."
            }
            post {
                always {
			emailext(
				subject : “Status of Security Scan Stage : ${currentBuild.result}”,
				body : “This security scan stage has been completed : ${currentBuild.result}”,
				attachLog : true,
				to : “${EMAIL}"
			)
                  
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo "Stage 5: Deploy to Staging - The application is deployed to a staging environment, specifically an AWS EC2 instance."
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo "Stage 6: Integration Tests on Staging - Additional integration tests are run in the staging environment to simulate a production environment."
            }
		post {
                always {
			emailext(
				subject : “Status of Integration Tests on Staging : ${currentBuild.result}”,
				body : “This Integration Tests on Staging has been completed : ${currentBuild.result}”,
				attachLog : true,
				to : “${EMAIL}"
			)
                  
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                echo "Stage 7: Deploy to Production - The final deployment is made to a production server, also an AWS EC2 instance."
            }
        }
    }
}
