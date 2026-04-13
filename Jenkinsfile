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

        stage('Build') {
            steps {
                sh 'rm -f dependency-reduced-pom.xml || true'
                sh 'mvn clean compile dependency:copy-dependencies'
            }
        }

        stage('Verify Build') {
            steps {
                sh 'ls target/classes/com/example/'
            }
        }

        stage('Run Application') {
            steps {
                sh 'java -cp target/classes:target/dependency/* com.example.App'
            }
        }
    }

    post {
        success {
            echo 'Build and execution successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
