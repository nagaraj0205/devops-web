pipeline {
    agent any

    environment {
        IMAGE_NAME = "devops-web"
        CONTAINER_NAME = "devops-web-container"
    }

    stages {

        stage('Build Docker Image') {
            steps {
                sh '''
                docker build -t $IMAGE_NAME .
                '''
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker rm -f $CONTAINER_NAME || true

                docker run -d \
                  --name $CONTAINER_NAME \
                  -p 81:80 \
                  $IMAGE_NAME
                '''
            }
        }
    }
}
