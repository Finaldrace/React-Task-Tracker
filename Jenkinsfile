pipeline {
    agent {
        docker {
            image 'node:6-alpine' 
            args '-p 3000:3000' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                sh 'npm install' 
            }
        }
        stage('Deploy'){
            steps {
                sh 'docker build -t react-app --no-cache .'
                sh 'docker tag react-app localhost:5000/react-app'
                sh 'docker push localhost:5000/react-app'
                sh 'docker rmi -f react-app localhost:5000/react-app'
            }
        }

    }
}