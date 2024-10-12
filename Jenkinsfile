pipeline {
    agent any

    stages {
        stage('Git Clone') {
            steps {
                echo 'Cloning Git Repository...'
                // Clone the repository from a Git source
                git branch: 'main', url: 'https://github.com/your-repo/your-project.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the project...'
                // Simulate a build failure
                echo 'Simulating Build Failure...'
                error 'Build Failed!' // This will intentionally fail the build
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // This stage will be skipped if the Build fails automatically
                sh 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying to server...'
                // This stage will also be skipped if the Build fails
                sh 'scp target/your-project.war user@server:/path/to/deploy/'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed during one of the stages. Check the logs for details.'
        }
    }
}
