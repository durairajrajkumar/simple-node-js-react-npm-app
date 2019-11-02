pipeline {
    agent any
    tools {nodejs "NodeJS10.16.3"}
    stages {
        stage('Build') { 
            steps {
                sh 'npm install --unsafe-perm --loglevel'
            }
        }
        stage('Test') { 
            steps {
                sh 'chmod 755 ./jenkins/scripts/test.sh'
                sh './jenkins/scripts/test.sh' 
            }
        }
        stage('Deliver') {
            steps {
                sh 'chmod 755 ./jenkins/scripts/deliver.sh'
                sh 'chmod 755 ./jenkins/scripts/kill.sh'
                sh './jenkins/scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}
