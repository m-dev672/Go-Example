node {
    def root = tool name: 'Go 1.18', type: 'go'
    stage('Preparation') { // for display purposes
        // Get some code from a GitHub repository
        git branch: 'main', url: 'https://github.com/m-dev672/GoExample/'
    }
    stage('Build') {
        // Run the maven build
        withEnv(["GOROOT=${root}", "GOPATH=${JENKINS_HOME}/jobs/${JOB_NAME}/builds/${BUILD_ID}/", "PATH+GO=${root}/bin"]) {
            sh 'go mod tidy'
            sh 'go build -o GoExample .'
        }
    }
    stage('Results') {
        archiveArtifacts 'GoExample'
    }
}
