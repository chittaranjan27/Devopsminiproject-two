pipeline {
    agent any
    tools {
        jdk 'jdk11'
        maven 'maven3'
    }

    stages {
        stage('SCM') {
            steps {
                git changelog: false, poll: false, url: 'https://github.com/chittaranjan27/Devopsminiproject-two.git'
            }
        }
        stage('Maven Build') {
            steps {
                echo 'Running Maven build...'
                
                bat 'mvn clean install'  
            }
        }
        stage('Docker Build & Push') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerhub_id') {
                        
                        bat "docker build -t chittaranjan027/shopping:latest1 ."
                        
                        bat "docker push chittaranjan027/shopping:latest1"
                    }
                }
            }
        }
    }
}