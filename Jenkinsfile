node('large') {
    currentBuild.result = "SUCCESS"
    try {
        stage('Checkout'){
            checkout scm
        }
        stage('Lint'){
            sh """
            source /home/jenkins/venv/molecule/bin/activate
            molecule lint
            """
        }
    }
    catch (err) {
        currentBuild.result = "FAILURE"
        throw err
    }
}