pipeline {
    agent any

    sh '/usr/bin/mvn clean package'

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/shashank485/newhello-world.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Docker Build & Run') {
            steps {
                sh '''
                docker build -t hello-java .
                docker run hello-java
                '''
            }
        }
    }
}
