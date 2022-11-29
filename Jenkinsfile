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
                sh "sudo docker build -t shaikharbaaz101/django:1 ."
            }
        }

        stage('docker push image') {
            steps {
                sh 'echo $DOCKER_PASSWORD | docker login -u $DOCKER_USER --password-stdin'
                sh "sudo docker push shaikharbaaz101/django:1"
            }
        }

        stage('deploy EC2') {
            steps {
                 echo 'itna hogaya'
            }
        }

    }
}
