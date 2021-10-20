pipeline { 
    environment { 
        registry = "mandarct/pipeline-demo" 
        registryCredential = 'mandarct' 
        ImageVersion = 'v1' 
        Image='pipeline-demo'
    }
    agent any 
    stages { 
        stage('Cloning our Git') { 
            steps { 
                git url: 'https://github.com/mandar-CT/python-MS.git' 
            }
        } 
        stage('Building our image') { 
            steps { 
                sh "docker build -t $Image ."
                }
            } 
        stage('Deploy our image') { 
            steps { 
                sh "docker push $registry:$ImageVersion"
                } 
            }
    }
}
