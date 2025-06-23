pipeline {
    agent any

    tools {
        maven 'Maven 3.8.1'
    }

    environment {
        SONAR_PROJECT_KEY = 'hello-java'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/shashank485/newhello-world.git'
            }
        }

        stage('Code Scan - SonarQube') {
            steps {
                withSonarQubeEnv('MySonarQube') {
                    sh 'mvn sonar:sonar -Dsonar.projectKey=$SONAR_PROJECT_KEY -Dsonar.java.binaries=target/'
                }
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Run App') {
            steps {
                sh 'java -jar target/*.jar'
            }
        }
    }
}
