pipeline {
    agent any

    stages {
        stage('Test stage') {
            steps {
                echo "Test string output 2"
                sh "go version"
                sh "go mod download"
                sh "go get github.com/nats-io/stan.go"
                sh "go build natsapp"
                echo "Hello, Ivan!"
            }
        }
    }
}