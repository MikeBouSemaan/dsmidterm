pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/Main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/MikeBouSemaan/dsmidterm.git']]])
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build('dsmid')
                }
            }
        }

        stage('Display Docker Image ID') {
            steps {
                script {
                    def dockerImageId = sh(script: "docker inspect --format='{{.Id}}' dsmid", returnStdout: true).trim()
                    echo "Docker Image ID: ${dockerImageId}"
                }
            }
        }
    }

    post {
        success {
            // Add post-build actions if needed
        }

        failure {
            // Add actions to perform on build failure
        }
    }
}
