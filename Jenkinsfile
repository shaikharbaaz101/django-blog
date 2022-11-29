pipeline {
    agent any
    
    environment {
        dockerr = credentials('dockerhub')
        DOCKER_USER = "$dockerr_usr"
        DOCKER_PASSWORD = "$dockerr_psw"
    }

    stages {
        stage('docker build image') {
            steps {
                sh "docker build -t shaikharbaaz101/django:2 ."
            }
        }

        stage('docker push image') {
            steps {
                sh 'echo $DOCKER_PASSWORD | docker login -u $DOCKER_USER --password-stdin'
                sh "docker push shaikharbaaz101/django:2"
            }
        }

        stage('deploy EC2') {
            steps {
                 sh "docker run -d -p 8000:8000 shaikharbaaz101/django:2"
            }
        }

    }
}
