pipeline {
    agent none
    stages {
        stage("Getting CLIMATE.md") {
            steps {
                webPage = sh(script: 'curl https://github.com/smartHomeHub/SmartIR/blob/master/docs/CLIMATE.md', returnStdout: true)
            }
        }
    }
}