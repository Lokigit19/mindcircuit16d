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
    success {
      mail to: 'machalvr@gmail.com',
           subject: "Jenkins: SUCCESS — ${currentBuild.fullDisplayName}",
           body: "Good news! Build succeeded: ${env.BUILD_URL}"
    }
    failure {
      mail to: 'machalvr@gmail.com',
           subject: "Jenkins: FAILURE — ${currentBuild.fullDisplayName}",
           body: "Build failed: ${env.BUILD_URL}"
    }
