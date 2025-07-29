pipeline {
    
    agent any

    tools {
        nodejs "Node_24"
    }

    stages {

        stage("Validate Version") {
            steps {
                echo "node --version"
                echo "npm --version"
            }
        } 

        stage("INSTALL") {
            steps {
                echo "npm install"
            }             
        }

        stage('BUILD') {
            steps {
                echo "npm run build"
            }
        }

        stage ("CLEANUP Workspace"){
            steps {
                echo "Work Space cleaned up"
            }
        }

        stage("NOTIFICATION") {
           steps {
            echo "Notified via email"
           } 
        }
    }
}