@Library("shared") _
pipeline {
    agent { label "vinod" }

    stages {
        stage("hello")
        {
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code") {
            steps {
                script{
                clone("https://github.com/mujeebalia123/node-todo-cicd.git","master")
                }
            }
        }

        stage("Build and Test") {
            steps {
                script{
                dockerBuild("node-app","latest","mujeebshaikh")  
            }
                
            }
            
        }

        stage("Scan Image") {
            steps {
                echo 'image scanning hogayi'
                // yahan trivy / snyk add kar sakte ho
            }
        }

        stage("Push") {
            steps {
              script{
                  dockerPush("node-app","latest","mujeebshaikh")
              }
            }
        }

        stage("Deploy") {
            steps {
                script{
                   dockerCompose()
                   echo 'code deploy hogaya' 
                }
                
                // kubectl / docker run commands yahan aayenge
            }
        }
    }
}
