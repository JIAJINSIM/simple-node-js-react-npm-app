pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // Ensure the repository is cloned to the Jenkins workspace
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/YOUR-GITHUB-ACCOUNT-NAME/simple-node-js-react-npm-app.git']]])
            }
        }
        stage('Build') {
            steps {
                sh 'ls -la'
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
        stage('Deliver') {
            steps {
                sh 'ls -la'
                sh './jenkins/scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}

