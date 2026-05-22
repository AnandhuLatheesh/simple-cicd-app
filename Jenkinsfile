pipeline 
{
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                url: 'YOUR_GITHUB_REPO_URL'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t cicd-demo-app .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker stop cicd-container || true
                docker rm cicd-container || true

                docker run -d \
                --name cicd-container \
                -p 80:80 \
                cicd-demo-app
                '''
            }
        }
    }
}