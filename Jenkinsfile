pipeline {
    agent any

    stages {
        stage("Checkout"){
            steps{
                sh "checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/sanjay2028/demobackend']])"
            }
        }
        stage("Build Image"){
            steps{
                sh "docker build . -t sanjay2028/demobackend"
            }
        }
    }

    post{
        always{
            echo "Thank you for using pipeline"
        }

        success{
            echo "Image was built successfully"
        }

        failure {
            echo "Failed to create a build"
        }

    }

}