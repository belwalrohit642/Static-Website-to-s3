pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from your Git repository
                checkout scm
            }
        }

        stage('Build and Test') {
            steps {
                // In a simple static website, there's no build step, so we'll skip it
                   sh 'npm install htmlhint stylelint'
                // Run tests to check HTML and CSS validity
                script {
                    try {
                        sh 'npx htmlhint index.html'  // Check HTML validity using htmlhint
             
                    } catch (Exception e) {
                        currentBuild.result = 'FAILURE'
                        error("Tests failed: $e")
                    }
                }
            }
        }
        stage('Deploy to AWS S3') {
            steps {
                script {
                    // Configure AWS CLI
                    sh 'aws configure set aws_access_key_id $AWS_ACCESS_KEY_ID'
                    sh 'aws configure set aws_secret_access_key $AWS_SECRET_ACCESS_KEY'
                    sh 'aws configure set default.region $AWS_DEFAULT_REGION'
                    sh 'pwd'
                    // Sync website files with S3
                    sh 'aws s3 cp /home/rohit/Documents/DocNexus/* s3://my-static-wesite-bucket-jenkins'
                }
            }
    }
}
}
