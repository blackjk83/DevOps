pipeline {
    agent { docker { image 'python:3.5.1' } }
    stages {
        stage('build') {
            steps {
                timeout(time: 3, unit: 'MINUTES') {
                    retry(5) {
                        sh 'python --version'
                    }
                }
            }
        }
    }
    post {
        always {
            echo 'Done with always'
            junit 'build/reports/**/*.xml'
        }
        success {
            echo 'Successful build'
        }
        failure {
            echo 'Failed build'
        }
        unstable {
            echo 'Unstable build'
        }
        changed {
            echo 'Some change were made...'
        }
    }
}

