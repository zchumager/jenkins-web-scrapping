
def deviceCompany = params.Device_Company

pipeline {
    agent any
    stages {
        stage("Getting CLIMATE.md") {
            steps {
                script {
                    currentBuild.displayName = "scrap_#$BUILD_NUMBER"

                    println("Device Company choosen: ${deviceCompany}")

                    gettingClimateMd(deviceCompany)
                }
            }
        }
    }
}

def gettingClimateMd(deviceCompany) {
    def webPage = sh(script: 'curl https://github.com/smartHomeHub/SmartIR/blob/master/docs/CLIMATE.md', returnStdout: true)

    def startIndex = webPage.indexOf("</a>${deviceCompany}</h4>")
    webPage = webPage[startIndex..-1]

    def endIndex = webPage.indexOf('<td>Broadlink</td>')
    webPage = webPage[0..endIndex-1]

    println("**************Web Page**************")
    println(webPage)

    def info = webPage

    startIndex = info.indexOf('<td><a')
    info = info[startIndex..-1]

    endIndex = info.indexOf('</a></td>')
    info = info[0..endIndex-1]

    println("**************Information**************")
    println(info)

    deviceCode = info.findAll("\\d+")[0]
    println("DEVICE CODE: ${deviceCode} for $deviceCompany")
}