pipeline {
	agent {
		node {
			label 'built-in'
			customWorkspace '/mnt/buildtool/project'
		}
	}
	stages {
		stage ('SCM Checkout') {
			steps {
				git 'https://github.com/akash-aws/project.git'
			}
		}
		stage ('mvn build') {
			steps {
				sh 'mvn clean package'
			}
		}
		stage ('artifact deploy') {
			steps {
				sh '''cp target/*.war /mnt/servers/apache-tomcat-9.0.69/webapps/project.war
				'''
			}
		}
	}
}
