pipeline {
    agent any

    environment {
        DOCKER_IMAGE_PREFIX = 'rubabzahra'
        KUBERNETES_NAMESPACE = 'k213832Namespace'
    }

    stages {
        stage('Build and Push Docker Images') {
            steps {
                script {
                    docker.build("${DOCKER_IMAGE_PREFIX}client", "./53832_frontend/client")
                    docker.build("${DOCKER_IMAGE_PREFIX}auth", "./53832_backend/Auth")
                    docker.build("${DOCKER_IMAGE_PREFIX}classrooms", "./53832_backend/Classrooms")
                    docker.build("${DOCKER_IMAGE_PREFIX}event-bus", "./53832_backend/event-bus")
                    docker.build("${DOCKER_IMAGE_PREFIX}post", "./53832_backend/Post")

                    docker.withRegistry('https://index.docker.io/v1/', DOCKER_HUB_CREDENTIALS) {
                        docker.image("${DOCKER_IMAGE_PREFIX}client").push()
                        docker.image("${DOCKER_IMAGE_PREFIX}auth").push()
                        docker.image("${DOCKER_IMAGE_PREFIX}classrooms").push()
                        docker.image("${DOCKER_IMAGE_PREFIX}event-bus").push()
                        docker.image("${DOCKER_IMAGE_PREFIX}post").push()
                    }
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                script {
                    def kubeconfig = readCredentials('kubernetes-credentials')
                    def kubectl = tool 'kubectl'
                    
                    sh "${kubectl} apply -f kubernetes-manifests/ --namespace ${KUBERNETES_NAMESPACE}"
                }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
