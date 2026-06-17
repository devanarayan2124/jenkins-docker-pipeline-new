pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t myapp:${BUILD_NUMBER} .'
            }
        }
    }

    post {

        success {
            echo 'Docker image built successfully'
        }

        failure {
            mail(
                to: 'devanarayan2124@gmail.com',
                subject: "Jenkins Build Failed: ${env.JOB_NAME}",
                body: """
                Build Number: ${env.BUILD_NUMBER}

                Job Name: ${env.JOB_NAME}

                Check Jenkins console output for details.
                """
            )
        }
    }
}
