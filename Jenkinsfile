pipeline{
	agent any
	environment {
		GIT_REPO = 'https://github.com/gitneo/qryos-1.git'
        GIT_BRANCH = 'master'
		APP_NAME = 'search-service'
		IMAGE_TAG = "${env.BUILD_NUMBER}"
	}
	stages{
		stage('Checkout Repository') {
			steps {
				echo "Checking out the repository..."
				git url: 'https://github.com/gitneo/bookstore.git', branch: 'master', credentialsId: 'github-pat'
			}
		}

		stage{'Build service'} {
			steps {
				echo "Building the service..."
				sh 'mvn clean package -DskipTests'
			}
		}

		stage('Test service') {
			steps {
				echo "Running tests..."
				sh 'mvn test'
			}
		}

		stage('Deploy service') {
			steps {
				sh 'docker build -t ${APP_NAME}:${IMAGE_TAG} .'
			}
		}
	}

	post{
		success{
			echo "Pipeline completed successfully!"
		}
		failure{
			echo "Pipeline failed. Please check the logs for details."
		}
	}
}