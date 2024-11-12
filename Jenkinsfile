pipeline {
    agent any

    stages {
        stage('Initialize') {
            steps {
                checkout scmGit(
                    branches: [[name: '**']], 
                    extensions: [], 
                    userRemoteConfigs: [[
                        credentialsId: 'Github-credentials', 
                        url: 'https://github.com/devbyaccident/Demo_Repo'
                    ]]
                )
            }
        }
        stage('Hello') {
            steps {
                echo "Hello World!"
                echo "This is build number $BUILD_NUMBER running in folder $WORKSPACE"
                sh("ls -altr")
            }
        }
        stage('HelloFromDev') {
            when {
                branch "dev"
            }
            steps {
                echo "Hello from the Dev branch!"
            }
        }
    }
    post {
      always {
        chuckNorris()
      }
    }
}
