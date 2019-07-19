
pipeline {
    agent any
    environment {
		def pom = readMavenPom file: 'pom.xml'
	}
   
   
    stages {
        stage("clone code") {
            steps {
                script {
                    // Let's clone the source
                    git 'https://github.com/rashmi7321/hello-world-war.git';
                }
            }
        }
        stage("mvn build") {
            steps {
                script {
                    // If you are using Windows then you should use "bat" step
                    // Since unit testing is out of the scope we skip them
                    sh "mvn clean install"
                }
            }
        }
        
        
    }
}
