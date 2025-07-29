pipeline {
    agent any

    stages {

        tools {
            nodejs "Node_24"
        }

        stage("Validate Version") {
            step {
                echo "node --version"
                echo "npm --version"
            }
        } 

        stage("INSTALL") {
            step {
                sh "npm install"
            }             
        }

        stage('BUILD') {
            step {
                sh "npm run build"
            }
        }

        stage ("CLEANUP Workspace"){
            step {
                echo "Work Space cleaned up"
            }
        }

        stage("NOTIFICATION") {
           step {
            echo "Notified via email"
           } 
        }
    }
}