pipeline {
    agent any

    stages {
        stage("Checkout"){
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/sanjay2028/demobackend']])
            }
        }
        stage("Build Image"){
            steps{
                sh "docker build . -t sanjay2028/demobackend"
            }
        }
        stage("Docker Hub"){
            scripts {
                withCredentials([string(credentialsId: 'sanjaydockerhub', variable: 'dockerhubpass.sanjay')]) {
                    sh "docker login -u sanjay2028 -p ${dockerhubpass.sanjay}"
                    sh "docker push sanjay2028/demobackend:${BUILD_ID}"
                }
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