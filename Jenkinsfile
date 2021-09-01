pipeline {
    agent { label 'docker-machine' } 
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
                sh 'docker rm $(docker stop $(docker ps -a -q --filter ancestor=examplenode --format="{{.ID}}"))'
                sh "docker run -d -p 3000:3000 --name node-app examplenode"
            }
        }
        stage('Testing') {
            steps {
                sh "curl http://localhost:3000"
                sh "npm test"
                echo " Testing Passed"
            }
        }
        stage('Deploy') {
            steps {
                sh "curl http://localhost:3000"
                echo "Server is up! & Running"
            }
        }
    }
}
