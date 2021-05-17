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
        stage('Sonar Analysis') {
            environment {
                scannerHome = tool 'SONAR_SCANNER'
            }
            steps {
                withSonarQubeEnv('SONA_LOCAL') {
                    bat "${scannerHome}/bin/sonnar-scanner -e -Dsonar.projectKey=DeployBack -Dsonar.host.url=http://localhost:9000 -Dsonar.login=5e5bf948e8c8ea00515b14647db9ebc3fbace912 -Dsonar.java.binaries=target -Dsonar.coverage.exclusions=**/.mvn/**,**/src/test/**,**/model/**,**Application.java"
                }                
            }
        }
    }
}