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
            post {
                always {
                    grafeasRecord "projects/mypipelinething"
                }
            }
        }
    }
}
