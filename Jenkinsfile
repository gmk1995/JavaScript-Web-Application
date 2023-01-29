pipeline {
    agent any
    tools {
        nodejs 'NodeJS-19.5.0'
    }
    environment {
        SONAR_HOST_URL = "http://3.110.40.247:9000"
    }
    stages {
        stage('GitCheckOut') {
            steps {
                git branch: 'main', credentialsId: '026f781b-368d-4626-ab66-08d71d1d7d82', url: 'https://github.com/gmk1995/JavaScript-Web-Application.git'
            }
        }
        stage('InstallNpmDependiences') {
            steps {
                sh "npm install"
                sh "npm install sonar-scanner"
            }
        }
        stage('SonarQubeReport') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh "sonar-scanner -Dsonar.host.url=$SONAR_HOST_URL"
                }
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
}
