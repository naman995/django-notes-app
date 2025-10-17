@Library("shared") _

pipeline {
    // agent { label 'ubuntu-agent' }
    agent any;

    stages {
        stage('Hello') {
            steps {
                script {
                    hello()
                }
            }
        }

        stage('Cloning') {
            steps {
                // echo 'Code Cloning'
                // git url: 'https://github.com/naman995/django-notes-app.git', branch:"main"
                script {
                    cloneRepo("https://github.com/naman995/django-notes-app.git", "main")
                }
            }
        }

        stage('Building') {
            steps {
                // echo 'Building'
                // sh 'docker build -t notes-app:latest .'
                script {
                    docker_build("notes-app", "latest", "naman1923")
                }
            }
        }

        stage('Testing') {
            steps {
                echo 'Testing the code'
                // Add test commands here if applicable
            }
        }

        stage('Pushing the Image to Docker Hub') {
            steps {
                // echo 'Pushing the Image to Docker hub'
                // withCredentials([usernamePassword('credentialsId':"dockerHubCred",passwordVariable:"dockerHubPass",usernameVariable:"dockerHubUser")]){
                // sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}"
                // sh "docker tag notes-app:latest ${env.dockerHubUser}/notes-app:latest"
                // sh "docker push ${env.dockerHubUser}/notes-app:latest"
                script {
                    docker_push("notes-app", "latest", "naman1923")
                }
            }
        }

        stage('Deploying') {
            steps {
                script {
                    docker_compose()
                }
            }
        }
    }
}
// This JenkinsFile use shared library
