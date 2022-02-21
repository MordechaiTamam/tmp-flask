pipeline {
    agent { label 'agent_1' }

    stages {
        stage('Docker build'){
            steps{
                sh 'ls -l'
                sh 'docker build -t hello-flask-160122 .'
            }
        }
        stage('API call') {
            agent {
                docker {
                    image 'hello-flask-160122'
                    reuseNode true
                }
            }
            steps {
                // sleep 20
                sh 'python /app/flask_app.py &'
                sleep 5
                sh 'curl 127.0.0.1:80'
            }
        }
    }
}
