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
                withSonarQubeEnv('sonarqube') {  
                    sh '''
                    cd backend
                    mvn clean package -DskipTests sonar:sonar   -Dsonar.projectKey=studentapp   -Dsonar.projectName=\'studentapp\'
                    '''
}
              }
        }
        stage('S3-Deploy')
        {
            steps {
                sh 'aws s3 cp backend/target/student-registration-backend-0.0.1-SNAPSHOT.jar  s3://amazon-bucket-1569/studemtapp.jar'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying done....'
            }
        }
    }
}
