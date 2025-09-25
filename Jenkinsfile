@Library("Shared") _
pipeline{
    agent { label "vinod" }
    
    stages{
        
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code"){
            steps{
                script{
                    clone("https://github.com/Jivesh24/django-notes-app.git" , "main")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                    docker_build("notes-app","latest","jivesh24")
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("notes-app", "latest", "jivesh24")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "Deploying Container"
                sh "docker compose up -d"
            }
        }
    }
}
