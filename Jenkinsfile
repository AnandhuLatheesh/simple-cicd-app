pipeline 
{
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t simple-cicd-app .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker stop simple-cicd-app-container || true
                docker rm simple-cicd-app-container || true

                docker run -d -p 80:80 \
                --name simple-cicd-app-container \
                simple-cicd-app
                '''
            }
        }
    }
}