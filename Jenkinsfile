
def defaults = [
    project: "projects/mypipelinething",
    name: "1.0.1-api",
    shortDescription: "",
    longDescription: "",
]

def image = "dtr.corp-us-east-1.aws.dckr.io/jenkins/binnacle:" + defaults["name"]

pipeline {
    agent "any"
    stages {
        stage("Hello") {
            steps{
                grafeasWrap {
                    sh "pwd"
                    sh "env"
                    sh "ls -lah"
                }
            }
        }
        stage("deploy"){
            steps{
                grafeasWrap {
                    sh "pwd"
                }
            }
            post {
                always {
                    grafeasImageNote  defaults + [image: image, type: "docker"]
                    grafeasDeploymentNote  defaults + [deployable: image]
                }
            }
        }
    }
    post {
        always {
            grafeasBuildOccurrence "projects/mypipelinething"
        }
    }
}
