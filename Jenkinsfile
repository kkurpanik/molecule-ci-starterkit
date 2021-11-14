node('large-node') {
    currentBuild.result = "SUCCESS"
    try {
        stage('Checkout'){
            checkout scm
        }
        stage('Lint'){
            sh 'source venv/molecule/bin/activate'
            sh 'molecule lint'
        }
    }
    catch (err) {
        currentBuild.result = "FAILURE"
        throw err
    }
}