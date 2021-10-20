pipeline { 
    environment { 
        registry = "mandarct" 
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
        stage('Building our image') { 
            steps { 
                sh "docker build -t $Image:$ImageVersion ."
                }
            } 
        stage('Tagging our image') { 
            steps { 
                sh "docker tag $Image $registry/$Image:$ImageVersion"
                }
            } 
        stage('Deploy our image') { 
            steps { 
                sh "docker push $registry/$Image:$ImageVersion"
                } 
            }
    }
}
