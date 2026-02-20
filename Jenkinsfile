@Library('my-shared-library')

pipeline {
    agent any

    tools {
        maven 'mvn399'   // Make sure Maven3 is configured in Global Tool Config
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Compile') {
            steps {
                mavenCompile()
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Output') {
            steps {
                sh 'java -jar target/my-app-1.0-SNAPSHOT.jar'
            }
        }
    }

    post {
        success {
            echo 'Build Successful ✅'
        }
        failure {
            echo 'Build Failed ❌'
        }
    }
}
