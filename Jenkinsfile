
def defaults = [
    project: "projects/mypipelinething",
    name: "1.1.2-web",
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
                    grafeasImageNote project: defaults.project, name: defaults.name, shortDescription: "short image note", longDescription: "long image note", image: image, type: "docker"
                    grafeasDeploymentNote project: defaults.project, name: defaults.name, shortDescription: "short deploy note", longDescription: "long deploy note", deployable: image
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
