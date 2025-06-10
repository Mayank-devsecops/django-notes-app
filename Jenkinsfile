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
                sh "docker pull mayank8765/notes-app:latest"
                sh "docker run -d -p 8000:8000 mayank8765/notes-app:latest"
                sh "docker ps"
                echo "********** CODE COMPELETED SUCCESFULL **********"
            }
        }
    }
}
