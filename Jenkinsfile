pipeline {
    agent any
    stages {
        stage("Getting CLIMATE.md") {
            steps {
                script {
                    currentBuild.displayName = "scrap_#$BUILD_NUMBER"
                    gettingClimateMd()
                }
            }
        }
    }
}

def gettingClimateMd() {
    def webPage = sh(script: 'curl https://github.com/smartHomeHub/SmartIR/blob/master/docs/CLIMATE.md', returnStdout: true)

    println("**************Web Page**************")

    /*
    
    def startIndex = webPage.indexOf('href="#mirage"')
    webPage = webPage[startIndex..-1]

    def endIndex = webPage.indexOf('<td>Broadlink</td>')
    webPage = webPage[0..endIndex]

    */
    
    println(webPage)
}