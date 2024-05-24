pipeline {
    agent {
        docker {
            image 'maven:3.9.6-jdk-8'
            args '-v /root/.m2:/root/.m2' // optional, to cache Maven dependencies
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
    }
}
