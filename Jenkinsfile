pipeline {
    agent{
        label 'AGENT-1'
    }
      options {
        timeout(time: 10, unit: 'SECONDS')  //this pipeline should complete 10 sec, if npot automatically fails  
        disableConcurrentBuilds()
        retry(2)
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo this is build'
                sh 'sleep 10'
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
            deleteDir()
        }
        success { 
            echo 'This section runs when pipeline success'
        }
        failure { 
            echo 'This section runs when pipeline failure'
        }
    }
}