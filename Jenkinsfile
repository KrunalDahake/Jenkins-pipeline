pipeline {
    agent any
    Tools {
        maven "MAVEN3"
    }
    satges {
        stage("Fetch code") {
            steps {
                git branch:"vp-rem" url:"https://github.com/devopshydclub/vprofile-repo.git"
            }
        }
        satge("Build") {
            steps {
                sh "mvn install -DskipTests"
            }
            post {
                success {
                    echo "Now its archiving"
                
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