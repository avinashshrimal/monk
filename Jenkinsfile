pipeline {
    agent any

    // Parameters to specify branch (optional)
    parameters {
        string(name: 'BRANCH_NAME', defaultValue: 'main', description: 'Branch to build')
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from the specified branch
                git branch: "${params.BRANCH_NAME}",
                    url: 'https://github.com/avinashshrimal/monk'
            }
        }

        stage('Build') {
            steps {
                // Example: run build commands (e.g. Maven, Gradle, npm)
                // Replace with your project's build tool
                echo 'Building the project...'
                sh './build.sh' // Or e.g. 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                // Example: run test commands
                echo 'Running tests...'
                sh './test.sh' // Or e.g. 'mvn test'
            }
        }
    }

    post {
        success {
            echo 'Build and tests completed successfully!'
        }
        failure {
            echo 'Build or tests failed.'
        }
    }
}
