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
         emailext(
            to: 'machalvr@gmail.com',
            subject: "Build ${currentBuild.currentResult}: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
             body: "The build has finished with status: ${currentBuild.currentResult}\n" +
                 "View the build details: ${env.BUILD_URL}"
                )
          }
     }
