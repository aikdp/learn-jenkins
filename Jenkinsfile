pipeline {
    agent{
        label 'AGENT-1'
    }
      options {
        timeout(time: 30, unit: 'MINUTES')  //this pipeline should complete 10 sec, if npot automatically fails  
        disableConcurrentBuilds()
        // retry(2)
    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
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
        stage('Parameters') {
            steps {
                echo "Hello ${params.PERSON}"

                echo "Biography: ${params.BIOGRAPHY}"

                echo "Toggle: ${params.TOGGLE}"

                echo "Choice: ${params.CHOICE}"

                echo "Password: ${params.PASSWORD}"
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