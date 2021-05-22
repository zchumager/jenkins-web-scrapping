pipeline {
    agent any
    stages {
        stage("Getting CLIMATE.md") {
            steps {
                script {
                    currentBuild.displayName = "scrapping-Job#$BUILD_NUMBER"
                    gettingClimateMd()
                }
            }
        }
    }
}

def gettingClimateMd() {
    def webPage = sh(script: 'curl https://github.com/smartHomeHub/SmartIR/blob/master/docs/CLIMATE.md', returnStdout: true)
    println("**************Web Page**************")
    def startIndex = webPage.indexOf("Mirage")
    webPage = webPage[startIndex..-1]
    
    println(webPage)
}