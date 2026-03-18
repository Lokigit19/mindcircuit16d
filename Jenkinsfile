pipeline {
    agent any

    tools {
        maven 'maven'
    }

    stages {

        stage('git clone') {
            steps {
                git branch: 'main', url: 'https://github.com/Lokigit19/mindcircuit16d.git'
            }
        }

        stage('Sonar scan') {
            steps {
                sh '''
                    mvn sonar:sonar \
                    -Dsonar.host.url=http://13.217.61.57:9000 \
                    -Dsonar.login=squ_4700821277ba17f610950314ccf251822e6c3e8a
                '''
            }
        }

        stage('Build Artifact') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Docker Image build') {
            steps {
                sh 'docker build -t loki1912/lokidoc:${BUILD_NUMBER} -f Dockerfile .'
            }
        }

        stage('Docker Image push') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-creds',
                    usernameVariable: 'USERNAME',
                    passwordVariable: 'PASSWORD'
                )]) {
                    sh '''
                        echo $PASSWORD | docker login -u $USERNAME --password-stdin
                        docker push loki1912/lokidoc:${BUILD_NUMBER}
                    '''
                }
            }
        }
    }   // ✅ properly closing stages

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
}
