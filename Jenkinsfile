pipeline {
    agent any

    triggers {
        cron('H/5 * * * *')     // build every 5 minutes
        pollSCM('H/2 * * * *')  // check repo every 2 minutes
    }

    stages {
        stage('Clone Repository') {
            steps { checkout scm }
        }

        stage('Build') {
            steps { echo "Build step running..." }
        }

        stage('Echo Build Status') {
            steps { echo "Build successful!" }
        }

        stage('Archive Artifacts') {
            steps {
                bat 'mkdir output & echo hello > output\\artifact.txt'
                archiveArtifacts artifacts: 'output/*.txt'
            }
        }
    }
}
