pipeline {
    agent any

    parameters {
        string(name: 'BRANCH_NAME', defaultValue: 'main', description: 'Branch to build')
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: "${params.BRANCH_NAME}",
                    url: 'https://github.com/avinashshrimal/monk'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the project...'
                // If you have a build.bat script in repo root:
                bat 'build.bat'
                
                // Or if you build with a command like Maven, uncomment this:
                // bat 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // If you have a test.bat script:
                bat 'test.bat'

                // Or run your test command directly, e.g.:
                // bat 'mvn test'
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
