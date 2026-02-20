@Library('my-shared-library') _

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
                mavenTest()
            }
        }

        stage('Package') {
            steps {
                mavenPackage()
            }
        }

        stage('Output') {
            steps {
                jarCheck()
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
