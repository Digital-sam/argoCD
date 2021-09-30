pipeline {
    agent any
    
    stages {
        stage('SCM checkout') {
            steps {
                checkout scm: //scm with necessary cred to https://github.com/do-community/node-mongo-docker-dev
            }
        }
        
        stage('build') {
            steps {
                container ('docker'){
                    // build new image
                    sh "docker build -t argoCD/Nodejs-Mongoapp:${env.GIT_COMMIT}

                }
            }
        }
        stage('deploy') {
            steps {
                sh "cd ./argoCD/NodeJs-Mongoapp && deployment edit set image argoCD/Nodejs-Mongoapp:${env.GIT_COMMIT}"
            }
        }
    }
}
