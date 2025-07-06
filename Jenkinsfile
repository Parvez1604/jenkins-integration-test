pipeline {
    agent any

    parameters {
        string(name: 'USERNAME', defaultValue: 'Parvez', description: 'Enter your name')
    }

    stages {
        stage('Welcome') {
            steps {
                sh """

                echo "Hello, ${params.USERNAME}!"
                """
            }
        }

        stage('System Info') {
            steps {
                sh """

                    echo "Gathering system info..."
                    uname -a
                    df -h
                    free -m
                """
            }
        }

        stage('Save Log') {
            steps {
                sh """

                echo "Run complete for ${params.USERNAME}" > 'result.txt'
                 """
                archiveArtifacts artifacts: 'result.txt'
               
            }
        }
    }
}
