
pipeline {
    agent any

    triggers {
        pollSCM('H/5 * * * *')
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build and Test') {
            steps {
                bat 'call "C:\\Users\\Yashwanth\\Downloads\\apache-maven-3.10.0-bin\\apache-maven-3.10.0\\bin\\mvn.cmd" clean test'
            }
        }

        stage('Package') {
            steps {
                bat 'call "C:\\Users\\Yashwanth\\Downloads\\apache-maven-3.10.0-bin\\apache-maven-3.10.0\\bin\\mvn.cmd" package'
            }
        }
    }

    post {
        success {
            echo 'Java CI/CD Pipeline completed successfully!'
            archiveArtifacts artifacts: 'target/*.jar',
                             allowEmptyArchive: true
        }

        failure {
            echo 'Java CI/CD Pipeline failed. Check the Console Output.'
        }
    }
}
