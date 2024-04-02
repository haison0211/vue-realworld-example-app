pipeline {
    agent {
        docker {
            image 'node:latest'
            args '-u root'
        }
    }
    
    stages {
        stage('Linting') {
            steps {
                echo "Run Linting"
                echo 'npm run lint'
            }
        }
        stage('Build') {
            steps {
                echo 'Build!!!'
                sh 'npm install'
                sh 'npm run build'
            }
        }
        stage('Unit Tests') {
            steps {
                echo 'Run Unit Tests!'
                sh 'npm test'
            }
        }
        stage('End-to-End Tests') {
            steps {
                echo 'Run End-to-End Tests!'
                echo 'npm run test:e2e'
            }
        }
    }
    
    post {
        always {
            archiveArtifacts 'dist/**' // Archive the 'dist' folder and all its contents
        }
    }
}
