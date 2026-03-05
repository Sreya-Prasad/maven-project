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
          bat 'mvn clean package -DskipTests'
        }
      }
      stage('Test'){
        steps{
          bat 'mvn test'
        }
      }
      stage('Install to Local Repo'){
        steps{
          bat 'mvn install'
        }
      }
    }
  }
    
