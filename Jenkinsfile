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
        stage('Notify') {
    steps {
        sh"""
        echo "Sending email to parwesking1233@gmail.com"\
        """
    }
}
        stage('Validation') {
    steps {
        script {
            def output = sh(script: 'free -m | grep Mem | awk \'{print $2}\'', returnStdout: true).trim()
            if (output.toInteger() < 1000) {
                error("Memory too low: ${output}MB — stopping build")
            } else {
                echo "Memory OK: ${output}MB"
            }
        }
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
