pipeline {
    agent{
        label 'AGENT-1'
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo this is build'
            }
        }
        stage('Test') {
            steps {
                sh 'echo this is test'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo this is deploy'
                // error "pipeline failed"
            }
        }
    }
    post { 
        always { 
            echo 'This section runs always'
        }
        success { 
            echo 'This section runs when pipeline success'
        }
        failure { 
            echo 'This section runs when pipeline failure'
        }
    }
}