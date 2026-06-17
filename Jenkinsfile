 pipeline {
    agent any

    environment {
        IMAGE_NAME = "rajpatel1202/mern-ecommerce"
        IMAGE_TAG = "${BUILD_NUMBER}"
    }

    stages {

        stage('Build Docker Image') {
            steps {
                sh '''
                docker build -t $IMAGE_NAME:$IMAGE_TAG .
                '''
            }
        }

        stage('Docker Login') {
            steps {
                withCredentials([
                    usernamePassword(
                        credentialsId: 'docker_hub_id',
                        usernameVariable: 'DOCKER_USER',
                        passwordVariable: 'DOCKER_PASS'
                    )
                ]) {
                    sh '''
                    echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin
                    '''
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                sh '''
                docker push $IMAGE_NAME:$IMAGE_TAG
                '''
            }
        }

        stage('Deploy To Kubernetes') {
            steps {
                sh '''
                kubectl set image deployment/ecommerce-app \
                ecommerce-app=$IMAGE_NAME:$IMAGE_TAG \
                -n ecommerce
                '''
            }
        }

        stage('Verify Rollout') {
            steps {
                sh '''
                kubectl rollout status deployment/ecommerce-app -n ecommerce
                '''
            }
        }
    }
}
