pipeline {
    agent any
    tools {
        maven "MAVEN3"
    }
    stages {
        stage("Fetch code") {
            steps {
                git branch: "vp-rem" , url: "https://github.com/devopshydclub/vprofile-repo.git"
            }
        }
        stage("Build") {
            steps {
                sh "mvn install -DskipTests"
            }
            post {
                success {
                    echo "Now its archiving"
                    archiveArtifacts artifacts: "**/target/*.war"
                }
            }
        }
        stage("Unit Test"){
            steps{
                sh "mvn test"
            }
        }
        stage("Integration Test"){
            steps{
                sh "mvn verify -DskipUnitTests"
            }
        }
    }
}