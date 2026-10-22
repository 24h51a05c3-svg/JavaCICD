
pipeline {
    agent any

    triggers {
        pollSCM('H/5 * * * *')
    }

    options {
        skipDefaultCheckout(true)
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build and Test') {
            steps {
                bat 'call "C:\\Users\\Yashwanth\\.vscode\\extensions\\oracle.oracle-java-27.0.0\\nbcode\\java\\maven\\bin\\mvn.cmd" clean test'
            }
        }

        stage('Package') {
            steps {
                bat 'call "C:\\Users\\Yashwanth\\.vscode\\extensions\\oracle.oracle-java-27.0.0\\nbcode\\java\\maven\\bin\\mvn.cmd" package'
            }
        }
    }

    post {
        success {
            archiveArtifacts artifacts: 'target/*.jar', allowEmptyArchive: true
            echo 'Java CI/CD Pipeline completed successfully!'
        }

        failure {
            echo 'Java CI/CD Pipeline failed. Check the Console Output.'
        }
    }
}
