pipeline {
    agent any

    stages {
        stage('Tests Backend') {
            steps {
                bat 'mvnw clean test'
            }
        }
        stage('Build Backend') {
            steps {
                bat 'mvnw package -DskipTests=true'
            }
        }
    }
}
