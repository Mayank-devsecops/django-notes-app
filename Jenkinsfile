@Library("Shared") _ 
pipeline{
    agent {label "Montu"}
    
    stages{
        stage("Code"){
            steps{
                script{
                    Code_Clone("https://github.com/MaYaNk-ai-tech/django-notes-app.git","main")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                    Docker_build("notes-app","latest","mayank8765")
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    Docker_Push("notes-app","latest","mayank8765")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "And finnaly the code is gonna deploy from here"
                sh "docker compose down --timeout 0 && docker compose up -d "
                sh "docker ps"
                echo "Code successfully compelete."
            }
        }
    }
}
