pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo "This is Build Stage"
                echo env.BUILD_NUMBER
            }
        }
        stage('Test') {
            steps {
                echo "This is Test Stage"
                echo "The Workspace is: ${env.WORKSPACE}"
            }
        }
        stage('Deploy') {
            steps {
                echo "This is Deploy Stage"
                echo "the Build Result is: ${currentBuild.currentResult}"
            }
        }
    }
}
