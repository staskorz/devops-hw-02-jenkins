pipeline {
    agent any

    parameters {
        string(defaultValue: 'user@example.com', description: 'Recipient mail', name: 'mail')
    }

    stages {
        stage('Print "Hello World"') {
            steps {
                sh "echo 'Hello World'"
            }
        }

        stage('Create file') {
            steps {
                //sh "date > /tmp/jenkins_was_here"
                sh "exit 1"
            }
        }
    }

    post {
        failure {
            mail to: ${params.mail},
            subject: 'The Pipeline failed :(',
            body: 'Something went wrong...'
        }
    }
}
