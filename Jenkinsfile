pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Downloading dependencies and building"
                sh "go mod download"
                sh "go get github.com/nats-io/stan.go"
                sh "go build -o nats-app"
                echo "Successful building nats-streaming-app"
            }
        }

        stage('Deployment') {
                    steps {
                        echo "Connecting to devops-server by SSH"
                        sh "sudo ssh -tt temon01@51.250.86.139"
                        echo "Successful connection to devops-server"

                        echo "Check pwd test with sudo"
                        sh "pwd"


                    }
                }
    }
}