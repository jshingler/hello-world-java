pipeline {
    agent any

    parameters {
            string(name: 'BRANCH_NAME', defaultValue: 'main', description: 'Branch to build')
        }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/jshingler/hello-world-java.git', branch: 'main'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
