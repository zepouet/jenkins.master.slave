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
            steps {
                node('slave1') {
                    sh 'echo "HelloWorld1"' 
                }
            }
        }

        stage ('Hello World Slave 2') {
            steps {
                node('slave2') {
                    sh 'echo "HelloWorld2"' 
                }
            }
        }

        stage ('Hello World Parallel') {
            steps {
                node('slave1') {
                    sh 'sleep 5&& echo "HelloWorld0"' 
                }
                node('slave2') {
                    sh 'echo "HelloWorld0"' 
                }
            }
        }

    }
}
