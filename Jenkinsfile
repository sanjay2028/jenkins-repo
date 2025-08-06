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
                script {
                    env.IMAGE_NAME = "sanjay2028/demobackend:${env.BUILD_ID}"
                    sh "docker build . -t ${env.IMAGE_NAME}"
                }                
            }
        }

        stage("Trivy Scan"){
            steps{
                sh """
                    trivy image --exit-code 1 --severity HIGH,CRITICAL --no-progress ${env.IMAGE_NAME}
                """
            }
        }

        stage("Docker Hub"){
            steps{
                script {
                    withCredentials([string(credentialsId: 'sanjaydockerhub', variable: 'dockerhubpass')]) {
                        sh """
                            echo ${dockerhubpass} | docker login --username sanjay2028 --password-stdin 
                            docker push sanjay2028/demobackend:${env.BUILD_ID}
                        """
                    }
                }
            }           
        }

        stage("Clean Up"){
            steps{
                script{
                    sh """
                        docker rmi -f ${env.BUILD_ID}
                    """
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