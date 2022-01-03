@Library('jenkins-shared-library@feature/shared_library') _

node('large') {
    currentBuild.result = "SUCCESS"
    try {
        stage('Checkout'){
            checkout scm
        }
        stage('CI-Test'){
            sh """
            source /home/jenkins/venv/molecule/bin/activate
            cd starterkit-role
            molecule test
            """
        }
    }
    catch (err) {
        currentBuild.result = "FAILURE"
        notifySlack "FAILURE"
        throw err
    } finally {
        notifySlack "SUCCESS"
    }
}