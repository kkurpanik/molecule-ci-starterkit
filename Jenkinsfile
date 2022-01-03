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
        throw err
    } finally {
        slackSend(color: "good", message: "Test message from Jenkins!")
    }
}