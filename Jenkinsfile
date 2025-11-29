pipeline {
    agent any
    tools{
        maven 'mvn1'
    }

    stages {
        stage('git clone') {
            steps {
                git branch: 'main', url: 'https://github.com/Lokigit19/mindcircuit16d.git'
            }
        }
     stage('mvn build') {
            steps {
                sh 'mvn clean install'
            }
        }
    stage('sonar scan') {
            steps {
                echo 'scan is done'
            }
        }
    stage('tar deployed') {
            steps {
                echo 'tar is deployed'
            }
        }
    }
}
post {
        always {
            echo 'Pipeline finished (always runs)'
        }
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
