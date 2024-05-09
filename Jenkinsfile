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

                echo "Check who am i after ssh connection."
                sh "whoami"

                echo "Check pwd test with jenkins ssh keys generated"
                sh "pwd"

                sh "scp /var/lib/jenkins/workspace/nats-streaming/nats-app temon01@51.250.86.139:/home/temon01/nats-builded"
                echo "Successful copying"

                sh "cd /var/lib/jenkins/workspace/nats-streaming"
                sh "pwd"
                sh "nohup ./nats-app &"
                echo "Successful starting nats-app 2"

                sh "sudo telnet localhost 4222"

                // ПРОВЕРИТЬ ПРАВИЛЬНО ЛИ СОЗДАН И ЗАПУЩЕН СЕРВЕР



                 sh '''
ssh -tt temon01@51.250.86.139 << EOF
whoami
pwd
cd /var/lib/jenkins/workspace/nats-streaming
pwd
nohup ./nats-app &
echo "Successful starting nats-app 1"
sudo telnet localhost 4222
exit
EOF
                 '''
                 echo "WORKING"
            }
        }
    }
}