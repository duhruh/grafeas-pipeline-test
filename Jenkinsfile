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
            post{
                success{
                    grafeasImageNote  
                        project: "projects/mypipelinething", 
                        name: "1.0.1-web", 
                        shortDescription: "", 
                        longDescription: "",
                        image: "dtr.corp-us-east-1.aws.dckr.io/jenkins/binnacle:1.0.1-web",
                        type: "docker"
                }
            }
        }
        post {
            always {
                grafeasBuildOccurrence project: "projects/mypipelinething"
            }
        }
    }
}
