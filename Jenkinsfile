pipeline {
    agent any
    tools {
        jdk 'jdk11'
        maven 'maven3'
    }

    stages {
        stage('SCM') {
            steps {
                git changelog: false, poll: false, url: 'https://github.com/chittaranjan27/Dockerminiproject.git'
            }
        }
        stage('Maven Build') {
            steps {
                echo 'Running Maven build...'
                // Execute Maven build
                bat 'mvn clean install'  // Use 'sh' if on Linux/Mac
            }
        }
        stage('Docker Build & Push') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerhub_id') {
                        // Build the Docker image
                        bat "docker build -t chittaranjan027/miniproject:latest1 ."
                        // Push the Docker image to Docker Hub
                        bat "docker push chittaranjan027/miniproject:latest1"
                    }
                }
            }
        }
    }
}
