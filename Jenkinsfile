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

                // Run tests to check HTML and CSS validity
                script {
                    try {
                        sh 'npx htmlhint index.html'  // Check HTML validity using htmlhint
                        sh 'npx stylelint style.css'   // Check CSS validity using stylelint
                    } catch (Exception e) {
                        currentBuild.result = 'FAILURE'
                        error("Tests failed: $e")
                    }
                }
            }
        }
    }
}
