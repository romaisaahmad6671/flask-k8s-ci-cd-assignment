pipeline {
    agent any

    environment {
        IMAGE_NAME = "flask-app:latest"
    }

    stages {

        stage('Build Docker Image') {
            steps {
                echo "Building Docker image..."
                sh "docker build -t ${IMAGE_NAME} ."
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                echo "Applying Kubernetes manifests..."
                sh "kubectl apply -f kubernetes/deployment.yaml"
                sh "kubectl apply -f kubernetes/service.yaml"
            }
        }

        stage('Verify Deployment') {
            steps {
                echo "Checking rollout status..."
                sh "kubectl rollout status deployment/flask-app"

                echo "Listing pods..."
                sh "kubectl get pods -o wide"

                echo 'Listing services...'
                sh "kubectl get svc"
            }
        }
    }

    post {
        success {
            echo "Deployment to Kubernetes was successful!"
        }
        failure {
            echo "Deployment failed!"
        }
    }
}
