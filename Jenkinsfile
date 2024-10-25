pipeline {
    agent any
    tools {
        jdk 'OpenJDK11'
        maven 'Maven3'
    }

    stages {
        stage('SCM') {
            steps {
                git changelog: false, poll: false, url: 'git@github.com:chittaranjan27/Devopsminiproject-two.git'
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
                    withDockerRegistry(credentialsId: 'aa12fd4c-6a73-43a6-82d3-5f917a65e9bd') {
                        
                        bat "docker build -t abhishek0083/abhi:tag123 ."
                        
                        bat "docker push abhishek0083/abhi:tag123"
                    }
                }
            }
        }
    }
}
