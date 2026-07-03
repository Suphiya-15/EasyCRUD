pipeline {
    agent any

    stages {
        stage('Pull') {
            steps {
                echo 'Pulling sccessful'
            }
        }
        stage('Build') {
            steps {
                sh '''
                cd backend
                mvn package -DskipTests
                '''
            }
        }
        stage('Test') {
            steps {
                withSonarQubeEnv(credentialsId: 'sonar-cred') {    
                     sh '''cd backend 
              mvn clean package -DskipTests sonar:sonar   -Dsonar.projectKey=studentapp   -Dsonar.projectName=\'studentapp\'
}
              }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying done....'
            }
        }
    }
}
