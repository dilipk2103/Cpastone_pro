pipeline {
    agent any

    tools {
        maven 'Maven 3.8.6'  // Make sure this matches your Jenkins config
        jdk 'jdk11'           // Make sure this matches your Jenkins config
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/dilipk2103/CapStone_project.git', branch: 'master'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean compile'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'mvn test -DsuiteXmlFile=testng.xml'
            }
        }

        stage('Publish Reports') {
            steps {
                junit 'test-output/testng-results.xml'
            }
        }
    }

    post {
        success {
            echo 'Build and tests passed!'
        }
        failure {
            echo 'Build or tests failed!'
        }
    }
}
