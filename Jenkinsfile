pipeline {
    agent any

    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/gauravkhandate/new_project.git'
            }
        }
        
        stage('Compile') {
            steps {
                sh 'mvn clean compile'
            }
        }
        stage('Unit Test') {
            steps {
                sh 'mvn test -DskipTests=true'
            }
        }
        stage ('Build Application') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage ('Slack') {
            steps {
            script {
                 slackSend channel: 'devops-slack', message: 'Done'
            }
        }
    }
}
