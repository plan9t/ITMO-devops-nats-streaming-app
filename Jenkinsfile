pipeline {
    agent any

    stages {
        stage('Test stage') {
            steps {
                echo "Downloading dependencies and building"
                sh "go mod download"
                sh "go get github.com/nats-io/stan.go"
                sh "go build -o /home/temon01/go_builded"

                echo "Команда для подключения по SSH: ssh temon01@51.250.86.139"
            }
        }
    }
}