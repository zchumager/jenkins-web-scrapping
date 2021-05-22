
// GETTING THE VALUE OF THE ATTRIBUTE Device_Company FROM params OBJECT
def deviceCompany = params.Device_Company

// GROOVY CLOSURE (CALLBACK) USED AS ENTRYPOINT
pipeline {
    // THE AGENT IS THE MACHINE WHERE THE CODE IN SCRIPT SECTION IS BEING EXECUTED
    agent any

    stages {
        stage("Getting CLIMATE.md") {
            steps {
                // IN THIS SECTION THE SHELL SCRIPT LOGIC IS DEFINED IN GROOVY DSL (DOMAN SPECIFIC LANGUAGE)
                script {
                    // CHANGES THE CONTENT OF THE JOB'S EXECUTION TITLE
                    currentBuild.displayName = "scrap_#$BUILD_NUMBER"

                    println("Device Company choosen: ${deviceCompany}")

                    gettingClimateMd(deviceCompany)
                }
            }
        }
    }
}

def gettingClimateMd(deviceCompany) {
    // sh IS A GROOVY DSL FUNCTION USED TO EXECUTE SHELL SCRIPT COMMANDS
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

    // \\d+ IS THE REGEX EXPRESSION USED TO EXTRACT JUST THE NUMBER OF THE CODE
    deviceCode = info.findAll("\\d+")[0]
    println("DEVICE CODE: ${deviceCode} for $deviceCompany")
}