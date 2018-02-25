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
                sh 'date > /tmp/jenkins_was_here'
            }
        }
    }

    post {
        failure {
            step(step([$class: 'Mailer',
                notifyEveryUnstableBuild: true,
                recipients: "${params.mail}",
                sendToIndividuals: true]))
        }
    }
}
