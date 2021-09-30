pipeline {
    agent any
    
    stages {
        stage('SCM checkout') {
            steps {
                checkout scm: [$class: 'GITSCM',userRemoteConfigs: [[credentialsId: 'github-ssh-key', url: 'git@github.com:Digital-sam/declarative_CICD.git']]]
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
                echo 'this is the deployment stage'
            }
        }
    }
}
