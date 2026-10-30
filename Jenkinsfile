pipeline {
    agent any

    stages {

        stage('Checkout Verification') {
            steps {
                sh 'echo "Repository successfully cloned"'
                sh 'pwd'
                sh 'ls -la'
            }
        }

        stage('Quality Gate') {
            steps {
                sh '''
                echo "Checking project structure..."

                test -f calculator.py
                test -f hello.py

                echo "Project structure validated"
                '''
            }
        }

        stage('Build Report') {
            steps {
                sh '''
                mkdir -p reports

                echo "Build Number: $BUILD_NUMBER" > reports/build_report.txt
                echo "Job Name: $JOB_NAME" >> reports/build_report.txt
                echo "Build Date: $(date)" >> reports/build_report.txt

                cat reports/build_report.txt
                '''
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully'
        }

        failure {
            echo 'Pipeline failed'
        }
    }
}
