@Library("Shared") _
pipeline{
    agent { label 'vinod'}
    stages{
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
            
        }
        stage("Code")
        {
            steps{
                script{
                    clone("https://github.com/jagsingh01/django-notes-app.git","main")
                }
            }
        }
        stage("Build")
        {
            steps{
                script{
                  docker_build("notes-app","latest","jagsingh01")
                }
            }
        }
        stage("Push to DockerHub")
        {
            steps{
                script{
                    docker_push("notes-app","latest","jagsingh01")
                }
            }
        }
        stage("Deploy")
        {
            steps{
                echo "This is deploying the code by Jagpreet"
                sh "docker compose down && docker compose up -d"
                
            }
        }
        
    }
}
