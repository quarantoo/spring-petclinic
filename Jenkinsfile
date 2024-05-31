pipeline {
    agent any

    environment {
        MAVEN_HOME = 'C:\\Program Files\\Maven\\apache-maven-3.9.6'
        PATH = "${env.MAVEN_HOME}\\bin;${env.PATH}"
    }

    stages {
        stage('Clone repo') {
            steps {
                git branch: 'main', credentialsId: '36224503-e5e8-4944-9e28-f2fdf613435a', url: 'https://github.com/quarantoo/spring-petclinic.git'
            }
        }
        stage('Build') {
            steps {
                bat 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }
        stage('Package') {
            steps {
                bat 'mvn package'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
            junit '**/target/surefire-reports/*.xml'
        }
    }
}
