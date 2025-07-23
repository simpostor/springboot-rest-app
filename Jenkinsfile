pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {
        stage('Checkout from GitHub') {
            steps {
                git branch: 'main', url: 'https://github.com/simpostor/springboot-rest-app'
            }
        }

        stage('Build with Maven (skipping tests)') {
            steps {
                // Use 'bat' for Windows
                bat 'mvn clean package -DskipTests'
            }
        }

        stage('Run Application') {
            steps {
                // This command will start your application
                bat 'java -jar target/10-springboot-rest-app-0.0.1-SNAPSHOT.jar'
            }
        }
    }

    post {
        always {
            // This still saves the JAR as an artifact
            archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
        }
    }
}