@Library('jenkins-shared-library@feature/shared_library') _

node('large') {
    try {
        currentBuild.result = "STARTED"
        notifySlack(currentBuild.result)
        
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
        currentBuild.result = "FAILED"
        throw err
    } finally {
        notifySlack(currentBuild.result)
    }
}