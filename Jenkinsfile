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
      script {
        def buildStatus = currentBuild.currentResult
        def buildUser = currentBuild.getBuildCauses('hudson.model.Cause$UserIdCause')

        emailext(
          subject: "Jenkins: ${buildStatus} — ${currentBuild.fullDisplayName}",
          body: """Good news! Build finished with status: ${buildStatus}
Link to build: ${env.BUILD_URL}
""",
          to: 'machalvr@gmail.com',
          from: 'machalvr@gmail.com'
        )
      }
    }
  }
