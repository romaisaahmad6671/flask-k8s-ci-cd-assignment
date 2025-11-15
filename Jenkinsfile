pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                echo "Simulating Docker build (Docker not installed in Jenkins container)..."
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
                echo "Verifying rollout..."
                sh "kubectl rollout status deployment/flask-app"

                echo "Listing pods..."
                sh "kubectl get pods -o wide"

                echo "Listing services..."
                sh "kubectl get svc"
            }
        }
    }

    post {
        success {
            echo "🎉 Deployment completed successfully!"
        }
        failure {
            echo "❌ Deployment failed!"
        }
    }
}

