
def defaults = [
    project: "projects/mypipelinething",
    name: "1.1.1-6-g6878738-api",
    image: "dtr.corp-us-east-1.aws.dckr.io/jenkins/binnacle:1.1.1-6-g6878738-api"
]

def imageNote = [
    project: defaults.project, 
    name: "image:"+defaults.name, 
    shortDescription: "short image note", 
    longDescription: "long image note", 
    image: defaults.image, 
    type: "docker",
]

def deploymentNote = [
    project: defaults.project,
    name: "deployment:"+defaults.name,
    shortDescription: "short deploy note",
    longDescription: "long deploy note", 
    deployable: defaults.image
]

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
                    grafeasImageNote(imageNote)
                    grafeasDeploymentNote(deploymentNote)
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
