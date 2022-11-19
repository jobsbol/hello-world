properties([pipelineTriggers([githubPush()])])
pipeline {
    agent any

    stages {
        stage('git clone') {
            steps {
                git 'https://github.com/jobsbol/hello-world'
            }
        }
        stage('build maven') {
            steps {
                sh "mvn clean install"
            }
        }
        stage('docker build') {
            steps {
                sh "docker build -t chetanpulsar3532/webapplication:latest ."
                sh "docker push chetanpulsar3532/webapplication:latest"
            }
        }
        stage('deploy container in kubernetes') {
            steps {
                sh "kubectl apply -f deployment.yaml"
            }
        }
    }
}
