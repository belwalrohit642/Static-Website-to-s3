pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Verify Node.js and npm') {
    steps {
        sh 'node -v'
        sh 'npm -v'
    }
}

        stage('Build') {
            steps {
              sh 'npm install'
              sh 'npm run build'
            }
        }
        stage('Test') {
            steps {
               sh 'htmlhint index.html'
               sh 'csslint styles.css'
            }
     
        }
        }
}

