pipeline {
    agent {
        docker {
            image 'node:lts-alpine'
            args '-u root'  // run as root to avoid permission issues
        }
    }
    stages {
        stage('Install bash') {
            steps {
                // Alpine uses `apk`, and we install bash because some Jenkins scripts expect it
                sh '''
                    apk update
                    apk add --no-cache bash
                '''
            }
        }
        stage('Run Node') {
            steps {
                // Now explicitly run via bash
                sh 'bash -c "node -v"'
            }
        }
    }
}
