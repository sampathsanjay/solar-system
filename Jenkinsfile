pipeline {
    agent any
    tools {
        nodejs 'NodeJS23.2.0'  // Make sure NodeJS is installed and configured in Jenkins tools
    }
    stages {
        stage('Installing Dependencies') {
            steps {
                // Install dependencies using npm
                sh 'npm install --no-audit'
            }
        }
    }
}

