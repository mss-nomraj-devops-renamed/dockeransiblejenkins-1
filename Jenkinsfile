pipeline{
    agent any
    tools {
  maven 'maven-3.9.3'
}
    environment {
      DOCKER_TAG = getVersion()
    }
    stages{
        stage('SCM'){
            steps{
                git 'https://github.com/Praveeen1996/dockeransiblejenkins-1.git'
            }
        }
        
        stage('Maven Build'){
            steps{
                sh "mvn clean package"
            }
        }
        
        stage('Docker Build'){
            steps{
                sh "docker build . -t praveenhema/webapps:${DOCKER_TAG} "
            }
        }
        
        
    }
}

def getVersion(){
    def commitHash = sh label: '', returnStdout: true, script: 'git rev-parse --short HEAD'
    return commitHash
}
