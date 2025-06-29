// Jenkinsfile
pipeline {
    // Here is the magic!
    // Instead of 'agent any', we specify a Docker agent.
    agent {
        docker {
            image 'node:16-alpine' // Use an official Node.js image (version 16, alpine is a small version)
        }
    }

    stages {
        stage('Verify Environment') {
            steps {
                echo 'Running build inside a Docker container!'
                // These commands are executed INSIDE the container, not on your Windows machine.
                sh 'node --version'
                sh 'npm --version'
            }
        }
        stage('Install Dependencies') {
            steps {
                // Jenkins automatically mounts the workspace, so npm can see package.json
                sh 'npm install'
            }
        }
        stage('Run Tests') {
            steps {
                // This runs the "test" script from our package.json
                sh 'npm test'
            }
        }
    }
}
