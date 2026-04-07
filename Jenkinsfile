@Library("shared") _
pipeline{
    agent {label "agent-vinod"}
    stages{
        stage("hello")
        {
            steps{
                script{
                    hello()
                }
            }
        }
        stage("code")
        {
            steps{
                script{
                    cloning("https://github.com/amanrajpd/django-notes-app-v2.git","dev")
                }
            }
        }
        stage("build")
        {
            steps{
                script
                {
                    Build_image("notes-app","latest")
                }
            }
        }
        stage("test")
        {
            steps{
            echo "Code testing"
            }
        }
        stage("pushing image")
        {
            steps{
                script{
                    push_image("notes-app","latest","amanrajpd")
                }
            }
        }
        stage("deploy")
        {
            steps{
            echo "Code deploying"
            sh "docker compose up -d"
            }
        }
    }
}
