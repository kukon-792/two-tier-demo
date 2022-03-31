pipeline {
    agent any

    stages {
        stage('docker-build') {
            steps {
                echo 'building docker image....'
                dir('kube-backend') {
                    script {
                        imgback = docker.build("kukonmiah11674/jenkins-pipeline-backend")
                    }
                }
            }
        }
        stage('docker-push') {
            steps {
                echo 'Push to dockerhub..'
                script {
                    docker.withRegistry('', 'kukon-dockerhub-cred') {
                        imgback.push()
                    }
                }
            }
        }
    }
}
