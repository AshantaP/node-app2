pipeline {
    agent any 
    stages {
        stage('Git-Clone') { 
            steps {
                sh "git clone https://github.com/AshantaP/node-app2.git"
            }
        }
        stage('Buiding-Docker Image') { 
            steps {
                sh "docker build -t examplenode ."
            }
        }
        stage('Runnning-Container') { 
            steps {
                sh "docker run -d -p 3000:3000 --name node-app examplenode"
            }
        }
        stage('Testing') {
            steps {
                sh "curl http://localhost:3000"
                sh "Testing Passed"
            }
        }
        stage('Deploy') {
            steps {
                sh "curl http://localhost:3000"
            }
        }
    }
}
