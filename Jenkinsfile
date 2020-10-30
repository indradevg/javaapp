pipeline {
    agent any
    
    tools {
        maven 'maven 3.6.3'
        jdk 'java 9'
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
    }
    
    post {
        always {
            archiveArtifacts artifacts: 'target/*.jar'
        }
    }
}
