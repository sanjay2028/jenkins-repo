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
                sh "npm install"
            }             
        }

        stage('BUILD') {
            steps {
                sh "npm run build"
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