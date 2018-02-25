agent any

stages {
    stage('Print "Hello World"') {
        steps {
            sh "echo 'Hello World'"
        }
    }

    stage('Create file') {
        steps {
            sh "date > /tmp/jenkins_was_here"
        }
    }
}

post {
    failure {
        mail to: 'john@example.com',
             subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
             body: "Something is wrong with ${env.BUILD_URL}"
    }
}
