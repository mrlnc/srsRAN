node {
    stage 'Checkout'
    // checkout the code we are currently running against
    checkout scm

    stage 'Build'
    // build Docker image and tag it with build number
    def app = docker.build "srs/srslte:${env.BUILD_NUMBER}"

    stage 'Test'
    // run tests
    app.inside {
        sh '/app/run_tests.sh'
    }
}
