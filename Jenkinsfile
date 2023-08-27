pipeline {
    agent {
            docker {
                image 'maven:3.9.3-eclipse-temurin-17-alpine'
                args '-v /root/.m2:/root/.m2'
            }
        }
    stages {

        stage('Directories') {
            steps {
                 sh "cd .."
                 sh "ls"
            }
        }
        stage('Build') {
            steps {
                sh "mvn clean install -DskipTests"
            }
        }
        stage('Test') {
            steps {
                sh "mvn test"
            }
        }
        stage('Deploy') {
            steps {
               echo 'Deploying!'
            }
        }
    }
}
