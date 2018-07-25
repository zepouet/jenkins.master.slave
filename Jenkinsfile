pipeline {

    agent any

    triggers {
        pollSCM('*/1 * * * *')
    }
    
    stages {

        stage ('Checkout') {
            steps {
                checkout scm
            }
        }

        stage ('Hello World Slave 1') {
            agent {
                label "slave1"
            }
            steps {
                sh 'echo "HelloWorld1"' 
            }
        }

        stage ('Hello World Slave 2') {
            agent {
                label "slave2"
            }
            steps {
                sh 'echo "HelloWorld2"'
            }
        }

        stage ('Hello World Parallel') {
            parallel {
               stage('Test On Slave 1') {
                   agent {
                       label "slave1"
                   }
                   steps {
                       sh 'sleep 5&& echo "HelloWorld0"' 
                   }
               }
               stage('Test On Slave 2') {
                   agent {
                       label "slave2"
                   }
                   steps {
                       sh 'echo "HelloWorld0"'
                   }
               }
            }
        }

    }
}
