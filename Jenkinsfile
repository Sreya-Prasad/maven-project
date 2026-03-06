pipeline {
    agent any

    tools {
        jdk 'JDK17'        // Make sure this name matches your configured JDK
        maven 'MAVEN_3'    // Make sure this name matches your configured Maven
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Sreya-Prasad/maven-project.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy stage goes here...'
                // e.g., sh 'scp target/*.jar ec2-user@<server>:/opt/apps/'
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }

    post {
        always {
            // Publish test results if you have Surefire reports
            junit testResults: 'target/surefire-reports/*.xml', allowEmptyResults: true
        }
        cleanup {
            // Optional: clean workspace after build
            cleanWs()  // requires Workspace Cleanup plugin
        }
    }
}
