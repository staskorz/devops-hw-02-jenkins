pipeline {
    agent any

    // parameters {
    //     string(defaultValue: 'user@example.com', description: 'Recipient mail', name: 'mail')
    // }

    stages {
        stage('Print "Hello World"') {
            steps {
                sh "echo 'Hello World'"
            }
        }

        stage('Create file') {
            steps {
                sh 'date > /tmp/jenkins_was_here'
                //sh 'exit 1'
            }
        }
    }

    post {
        always {
            mail(
                // to: "${params.mail}",
                to: "${env.NOTIFY_EMAIL}",
                subject: "Job '${env.JOB_NAME}' status '${currentBuild.currentResult}'",
                body: "Job '${env.JOB_NAME}' complete with status '${currentBuild.currentResult}'"
            )
        }
    }
}
