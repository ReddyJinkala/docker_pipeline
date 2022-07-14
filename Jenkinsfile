pipeline {
    agent any
    
     environment {
        registry = "smadhu29/mypythonapp"
        registryCredential = 'docker_hub'
        dockerImage = ''
    }

    stages {
        stage('checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/sappidi341/docker_pipeline']]])
            }
        }
        
        stage('Build docker image') {
            steps{
                script {
                dockerImage = docker.build registry
        }
            }
        }
        
         stage('Upload Docker Image to DockerHub') {
            steps{    
               script {
                 docker.withRegistry( '', registryCredential ) {
                 dockerImage.push()
            }
        }
      }
    }
    }
}
