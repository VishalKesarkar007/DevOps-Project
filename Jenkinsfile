pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/VishalKesarkar007/DevOps-Project.git'
            }
        }

        stage('Build Application') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Docker Build & Deploy') {
            steps {
                sh '''
                docker rm -f devopsapp || true
                docker build -t devopsapp .
                docker run -d -p 8087:8080 --name devopsapp devopsapp
                '''
            }
        }
    }
}
