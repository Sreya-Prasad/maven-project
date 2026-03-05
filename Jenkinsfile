pipeline {
    agent any

    tools {
        jdk 'JDK17'
        maven 'MAVEN_3'
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/<your-username>/<repo>.git'
            }
        }

        stage('Build Maven Project') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }
}
