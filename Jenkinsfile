pipeline{
  agent any
    tools{
      maven 'MAVEN_3_9'
      jdk 'JDK17'
    }
    stages{
      stage('Checkout Code'){
        steps{
          git 'https://github.com/Sreya-Prasad/maven-project.git'
        }
      }
      stage('Build'){
        steps{
          sh 'mvn clean package -DskipTests'
        }
      }
      stage('Test'){
        steps{
          sh 'mvn test'
        }
      }
      stage('Install to Local Repo'){
        steps{
          sh 'mvn install'
        }
      }
    }
  }
    
