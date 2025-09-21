pipeline {
    agent any

    stages {
        stage('git clone') {
            steps {
                git branch: 'main', url: 'https://github.com/Lokigit19/mindcircuit16d.git'
            }
        }
    stage('build tar') {
            steps {
                sh 'mvn clean install'
            }
        }
    }
}
