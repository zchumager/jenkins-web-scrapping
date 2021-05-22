
def deviceCompany = params.Device_Company

pipeline {
    agent any
    stages {
        stage("Getting CLIMATE.md") {
            steps {
                script {
                    currentBuild.displayName = "scrap_#$BUILD_NUMBER"

                    println("Device Company: ${deviceCompany}")

                    gettingClimateMd(deviceCompany)
                }
            }
        }
    }
}

def gettingClimateMd(deviceCompany) {
    def webPage = sh(script: 'curl https://github.com/smartHomeHub/SmartIR/blob/master/docs/CLIMATE.md', returnStdout: true)

    println("**************Web Page**************")

    def startIndex = webPage.indexOf("</a>${deviceCompany}</h4>")
    webPage = webPage[startIndex..-1]

    def endIndex = webPage.indexOf('<td>Broadlink</td>')
    webPage = webPage[0..endIndex-1]

    println(webPage)
}