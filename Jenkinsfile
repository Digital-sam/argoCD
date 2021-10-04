pipeline {
    agent any
    triggers {
        pollSCM 'H/10 * * * *'
    }
    stages {
        stage('checkout') {
            steps {
                checkout([
                    $class: 'SubversionSCM', 
                    additionalCredentials: [], 
                    excludedCommitMessages: '',
                    locations: [[
                        credentialsId: 'mySvnCredentials', 
                        depthOption: 'infinity',
                        ignoreExternalsOption: true, 
                        local: '.', 
                        remote: 'https://github.com/do-community/node-mongo-docker-dev']], 
                    workspaceUpdater: [$class: 'CheckoutUpdater']
                ])
            }
        }
    }
}
     
        stage('build') {
            steps {
                container ('docker'){
                    // delete older image
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
