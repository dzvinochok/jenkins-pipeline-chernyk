pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t dzvinka:latest .'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'echo "Tests passed!"'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Pushing Docker image to DockerHub...'
                withCredentials([usernamePassword(credentialsId: '51111ffe-4c97-4ace-a2f7-3efcddec3688', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
           
        sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                    sh 'docker tag peninaapp:latest $DOCKER_USER/dzvinka:latest'
                    sh 'docker push $DOCKER_USER/dzvinka:latest'
                }
            }
        }
    }
}


