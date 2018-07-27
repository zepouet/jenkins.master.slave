pipeline {
    agent any
    def label = "mypod-${UUID.randomUUID().toString()}"
	podTemplate(label: label, containers: [
	    containerTemplate(name: 'slave', image: 'streamout/jenkins-slave:1.0.0', ttyEnabled: true, command: 'cat')
	  ]) {

	    node(label) {
		stage('Get a Golang project') {
		    git url: 'https://github.com/hashicorp/terraform.git'
		    container('slave') {
		        stage('slave a Go project') {
		            sh """
		            whoami
		            docker version
		            """
		        }
		    }
		}

	    }
	}
}
