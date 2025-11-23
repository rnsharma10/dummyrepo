pipeline {
    agent any
    options {
        skipDefaultCheckout(true)
    }
    stages {
        stage('prepping the workspace'){
            steps{
                cleanWs()
            }
        }
        stage('fetching') {
            steps {
                checkout scm
            }
        }
        stage('type of change'){
            steps{
                script{
                    echo "===================================================="
                    if (env.CHANGE_ID){
                        env.BUILD_TYPE = "Pull request"
                        env.BUILD_REF = "🟢 PR-${env.CHANGE_ID}: from ${env.CHANGE_BRANCH} to ${env.CHANGE_TARGET}."
                    } 
                    else {
                        env.BUILD_TYPE = "Branch build"
                        env.BUILD_REF = "🟢 BRANCH: ${env.BRANCH_NAME}"
                        echo 
                    }
                    echo "===================================================="
                }


                sh """
                    echo "fetching ${env.BRANCH_NAME}"
                """

            }
        }
        stage('build') {
            steps {
                    sh """
                        echo "building"
                    """
            }
        }
        stage('test') {
            steps {
                    sh """
                        echo "testing"
                    """
            }
        }
        stage('deploy') {
            steps {
                    sh """
                        echo "deploying"
                    """
            }
        }
    }
    post{
        always{
            cleanWs(cleanWhenNotBuilt: false,
                    deleteDirs: true,
                    disableDeferredWipeout: true,
                    notFailBuild: true,
            )
        }
    }
}


