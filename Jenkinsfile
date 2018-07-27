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
        stage('Container exec') {
            agent {
                label "autoscale"
            }
            steps {
                container('slave') {
                    sh """
                    whoami
                    docker version
                    """
                }
            }
        }
        stage ('Hello World Slave 1') {
            agent {
                label "autoscale"
            }
            steps {
                sh 'hostname' 
            }
        }

        stage ('Hello World Slave 2') {
            agent {
                label "autoscale"
            }
            steps {
                sh 'hostname'
            }
        }

        stage ('Hello World Parallel') {
            parallel {
               stage('Test On Slave 1') {
                   agent {
                       label "autoscale"
                   }
                   steps {
                       sh 'sleep 10 && hostname' 
                   }
               }
               stage('Test On Slave 2') {
                   agent {
                       label "autoscale"
                   }
                   steps {
                       sh 'sleep 10 && hostname'
                   }
               }
            }
        }

    }
}

