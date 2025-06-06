pipeline {
    agent none  // We'll define agent per stage

    stages {
        stage('Node.js Stage') {
            agent {
                docker {
                    image 'node:22.16.0-alpine3.22'
                    args '-u root'
                }
            }
            steps {
                sh '''
                    apk add --no-cache bash
                    bash -c "echo Node Version: $(node -v)"
                '''
            }
        }

        stage('Maven Stage') {
            agent {
                docker {
                    image 'maven:3.9.6-eclipse-temurin-17-alpine'
                    args '-u root'
                }
            }
            steps {
                sh '''
                    apk add --no-cache bash
                    mvn -v
                '''
            }
        }
    }
}
