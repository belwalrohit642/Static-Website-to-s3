pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                  echo "Build the application"
                // For a simple static site, you might not need this stage
            }

        }
        stage('Test') {
            steps {
        sh 'npm install'
        sh 'npm run test'
        // If tests pass, create a build artifact
        catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
        sh 'npm run build' // Or any other command to generate build artifacts
                
            }
     
        }
        }
}
}
