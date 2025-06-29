pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                echo 'Cloning repository...'
            }
        }

        stage('Run Script') {
            steps {
                sh '''
                    echo "Running system info..."
                    uname -a
                    df -h
                    free -m
                '''
            }
        }

        stage('Archive Logs') {
            steps {
                sh 'echo "Pipeline completed" > output.txt'
                archiveArtifacts artifacts: 'output.txt', onlyIfSuccessful: true
            }
        }
    }
}

