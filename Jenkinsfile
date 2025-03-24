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
        stage('Run Audits in Parallel') {
            parallel {
                stage('NPM Dependency Audit') {
                    steps {
                        // Run npm audit for critical vulnerabilities
                        sh 'npm audit --audit-level=critical'
                    }
                }
                stage('OWASP Dependency Check') {
                    steps {
                        dependencyCheck additionalArguments:'''
                            --scan \'./\'
                            --out \'./\'
                            --format \'ALL\'
                            --prettyPrint''', odcInstallation: 'OWASP-10.0.3'
                    }
                }
            }
        }
    }
}

