pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean' 
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test' 
            }
        }
        stage('Package') {
            steps {
                sh 'mvn package' 
            }
        }
        stage('Deploy') {
            when {
                branch "master"
            }
            steps {
                sh 'mvn deploy' 
            }
        }
    }
    post {
        success {
            mail to: 'dimitrispy@hotmail.com',
                subject: "SUCCESSFUL: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
                body: """SUCCESSFUL: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':
                Check console output at ${env.BUILD_URL} ${env.JOB_NAME} [${env.BUILD_NUMBER}]"""
        }
        failure {
           mail to: 'dimitrispy@hotmail.com',
              subject: "FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
              body: """FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':
                Check console output at ${env.BUILD_URL}' ${env.JOB_NAME} [${env.BUILD_NUMBER}]"""
        }
    }
}


