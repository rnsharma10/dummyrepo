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
                sh """
                -----------------------------------------------
                ${env}
                -----------------------------------------------
                """
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
