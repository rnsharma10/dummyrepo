pipeline {
    agent any
    options {
        quiet()
        skipDefaultCheckout(true)
    }
    stages {
        stage('fetching') {
            steps {
                cleanWs()
                checkout scm
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
