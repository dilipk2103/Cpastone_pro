pipeline {
    agent any

    tools {
        maven 'Maven 3.8.6'  // Use the actual name you configured in Jenkins
        jdk 'JDK 11'         // Use the actual name you configured in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/dilipk2103/CapStone_project.git', branch: 'master'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'mvn test -DsuiteXmlFile=testng.xml'
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
