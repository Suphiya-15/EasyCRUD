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
               sh '''cd backend 
              mvn clean package -DskipTests sonar:sonar   -Dsonar.projectKey=studentapp   -Dsonar.projectName=\'studentapp\'   -Dsonar.host.url=http://65.0.117.141:9000   -Dsonar.token=sqp_eb351155f8e276ddd66c6cc1da6c6517e855a437'''
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying done....'
            }
        }
    }
}
