pipeline {
    agent any

    tools {
        maven 'Maven 3.8.1' // Make sure this is configured in Jenkins → Global Tool Configuration
    }

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/shashank485/newhello-world.git'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Run Java App') {
            steps {
                sh 'java -jar target/*.jar'
            }
        }
    }
}
