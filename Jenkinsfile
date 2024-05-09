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
                echo "Check who am i before ssh connection."
                sh "whoami"

                echo "Connecting to devops-server by SSH and execute whoami and pwd commands"
                sh "ssh -tt temon01@51.250.86.139 'whoami; pwd'"
                echo "Successful connection to devops-server"

                echo "Check who am in jenkins server"
                sh "whoami"

                echo "Check pwd in jenkins"
                sh "pwd"

                sh "scp /var/lib/jenkins/workspace/nats-streaming/nats-app temon01@51.250.86.139:/home/temon01/nats-builded"
                echo "Build successful copied"

                // ПРОВЕРИТЬ ПРАВИЛЬНО ЛИ СОЗДАН И ЗАПУЩЕН СЕРВЕР


                sh "ssh -tt temon01@51.250.86.139 'whoami; pwd; cd /var/lib/jenkins/workspace/nats-streaming; nohup ./nats-app &; sudo telnet localhost 4222'"
                echo "WORKING"
            }
        }
    }
}