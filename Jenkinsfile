pipeline { 
    environment { 
        registry = "mandarct/pipeline-demo" 
        registryCredential = 'mandarct' 
        ImageVersion = 'v1' 
        Image='pipeline-demo'
        gitCredentials = "CREDENTIAL_ID"
        repoUrl = "https://github.com/mandar-CT/python-MS.git"
        branchName = 'feature'
    }
    agent any 
    stages { 
        
        stage('Clone') {
            steps{
          echo 'Cloning files from (branch: "' + branchName + '" )'
          echo 'Make the output directory'
          sh 'mkdir -p build'
          dir('build') {
                git branch: branchName, credentialsId: 	gitCredentials, url: repoUrl
            } 
        }
      }       
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
