
pipeline {
    agent any

    triggers {
        pollSCM('H/5 * * * *')
    }

    stages {
        stage('Checkout') {
            steps {
                deleteDir()
                bat 'git clone --branch main https://github.com/24h51a05c3-svg/JavaCICD.git .'
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
            archiveArtifacts artifacts: 'target/*.jar',
                             allowEmptyArchive: true
            echo 'Java CI/CD Pipeline completed successfully!'
        }

        failure {
            echo 'Pipeline failed. Check Console Output.'
        }
    }
}
