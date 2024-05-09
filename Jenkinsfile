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

//                  echo "ЕЩЕ РАЗ Connecting to devops-server by SSH to execute multiple commands"
//                  sh '''
//                      ssh -tt temon01@51.250.86.139 << EOF
// whoami
// pwd
// exit
// EOF
//                  '''
//                  echo "WORKING"
            }
        }
    }
}