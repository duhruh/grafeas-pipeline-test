pipeline {
    agent "any"
    stages {
        stage("nothing"){
            steps{
                forget "nothing"
            }
        }
        stage("Hello") {
            steps{
                sh "env"
                grafeasWrap {
                    forget "this has been forgotten"
                    sh "pwd"
                }
            }
            post {
                always {
                    grafeasRecord "projects/mypipelinething"
                }
            }
        }
    }
}
