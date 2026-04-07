@Library("Shared") _
pipeline{
    agent { label 'prod' }
    
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
                    clone("https://github.com/md-faizan-repo/django-notes-app.git", "main")
                }
            }
        }
        stage("Build"){
            steps{
                //sh "whoami"
                script{
                    docker_build("notes-app", "latest", "mfaizan1999")
                }
            }
        }
        stage("Test"){
            steps{
                echo "This is test the code"
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("notes-app", "latest", "mfaizan1999")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                sh " docker compose down && docker compose up -d"
            }
        }
    }
}
