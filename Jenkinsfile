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
                  echo "Build the applicatio"
            }

        }
        stage('Test') {
            steps {
        sh 'htmlhint index.html' 
        sh 'csslint styles.css

            }
     
        }
        }
}
