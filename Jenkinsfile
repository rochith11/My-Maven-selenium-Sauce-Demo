pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/rochith11/My-Maven-selenium-Sauce-Demo.git'
            }
        }

        stage('Build & Test') {
            steps {
            	sh 'ls target/classes/com/example/'
                sh 'mvn clean compile'
            }
        }

        stage('Run Application') {
            steps {
                sh 'mvn clean compile exec:java -Dexec.mainClass=com.example.App -Dexec.classpathScope=compile'
            }
        }
    }

    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
