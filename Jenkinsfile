pipeline {
    agent any
    
    environment {
        PATH = "/Users/nitish.ugru/.rd/bin/docker:$PATH"
    }

    stages {
        stage('Without docker') {
            steps {
                sh '''
                  echo "Hello from outside container"
                  ls -al
                  touch hello1.txt
                '''
            }
        }
        
        stage('With docker') {
            agent {
                docker {
                    image "node:18-alpine"
                    reuseNode true
                }
            }

            steps {
                echo 'Hello from inside container'
                sh '''
                  ls -al
                  touch hello2.txt
                '''
            }
        }
    }
}

