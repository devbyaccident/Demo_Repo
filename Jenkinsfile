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
        stage('ReadFile') {
            steps {
                readFile './README.md'
            }

            post {
                always {
                    cleanWs(patterns: [[pattern: '*.md', type: 'EXCLUDE']])
                }
            }
        }
        stage('ListAgain') {
            steps {
              sh("ls -altr")
            }
        }
    }
    post {
      always {
        chuckNorris()
      }
    }
}
