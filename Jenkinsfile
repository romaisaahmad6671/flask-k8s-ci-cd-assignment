pipeline {
    agent any

<<<<<<< HEAD
    environment {
        IMAGE_NAME = "flask-app:latest"
    }

=======
>>>>>>> 57a7668 (Task 4: Update Jenkinsfile for Jenkins CD pipeline)
    stages {

        stage('Build Docker Image') {
            steps {
<<<<<<< HEAD
                echo "Building Docker image..."
                sh "docker build -t ${IMAGE_NAME} ."
=======
                echo "Simulating Docker build (Docker not installed in Jenkins container)..."
>>>>>>> 57a7668 (Task 4: Update Jenkinsfile for Jenkins CD pipeline)
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                echo "Applying Kubernetes manifests..."
<<<<<<< HEAD
                sh "kubectl apply -f kubernetes/deployment.yaml"
                sh "kubectl apply -f kubernetes/service.yaml"
=======
                sh 'kubectl apply -f kubernetes/deployment.yaml'
                sh 'kubectl apply -f kubernetes/service.yaml'
>>>>>>> 57a7668 (Task 4: Update Jenkinsfile for Jenkins CD pipeline)
            }
        }

        stage('Verify Deployment') {
            steps {
<<<<<<< HEAD
                echo "Checking rollout status..."
                sh "kubectl rollout status deployment/flask-app"

                echo "Listing pods..."
                sh "kubectl get pods -o wide"

                echo 'Listing services...'
                sh "kubectl get svc"
=======
                echo "Verifying rollout..."
                sh 'kubectl rollout status deployment/flask-app'
                sh 'kubectl get pods'
                sh 'kubectl get svc'
>>>>>>> 57a7668 (Task 4: Update Jenkinsfile for Jenkins CD pipeline)
            }
        }
    }

    post {
        success {
<<<<<<< HEAD
            echo "Deployment to Kubernetes was successful!"
        }
        failure {
            echo "Deployment failed!"
=======
            echo "🎉 Deployment completed successfully!"
        }
        failure {
            echo "❌ Deployment failed!"
>>>>>>> 57a7668 (Task 4: Update Jenkinsfile for Jenkins CD pipeline)
        }
    }
}
