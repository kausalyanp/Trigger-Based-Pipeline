pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/kausalyanp/Trigger-Based-Pipeline.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install' // Replace with your build command
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test' // Replace with your testing command
            }
        }
        stage('Code Analysis') {
            steps {
                sh 'mvn sonar:sonar' // Requires SonarQube plugin
            }
        }
        stage('Deploy') {
            steps {
                sshagent(credentials: ['your-ssh-credential-id']) {
                    sh 'scp target/*.war user@remote-server:/path/to/deploy'
                    sh 'ssh user@remote-server "systemctl restart tomcat"'
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution finished!'
        }
    }
}
