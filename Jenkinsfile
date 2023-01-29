pipeline {
    agent any

    tools {
        nodejs 'NodeJS-19.5.0'
    }

    stages {
        stage('GitCheckOut') {
            steps {
                git branch: 'main', credentialsId: '026f781b-368d-4626-ab66-08d71d1d7d82', url: 'https://github.com/gmk1995/JavaScript-Web-Application.git'
            }
        }
    }

    stage('InstallNpmDependiences') {
        steps {
            sh "npm install"
        }
    }

    stage('SonarQubeReport') {
        steps {
            sh "npm run sonar"
        }
    }

    stage('UploadArtifactsToNexus') {
        steps {
            sh "npm run publish"
        }
    }

    stage('StartingTheApp') {
        steps {
            sh "npm start"
        }
    }
}