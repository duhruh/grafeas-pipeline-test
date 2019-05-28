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
                    grafeasImageNote  project: "projects/mypipelinething",  name: "1.0.1-web", shortDescription: "This is short", longDescription: "this is long", image: "dtr.corp-us-east-1.aws.dckr.io/jenkins/binnacle:1.0.1-web", type: "docker"
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
