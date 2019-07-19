
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
                    git '';
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
        stage("publish to nexus") {
            steps {
               
                nexusPublisher nstepsexusInstanceId: 'nexusrepo', \
                nexusRepositoryId: 'mavenexample', \
                packages: [[$class: 'MavenPackage', \
                mavenAssetList: [[classifier: '', extension: '', \
                filePath: "target/${pom.artifactId}-${pom.version}.${pom.packaging}"]], \
               mavenCoordinate: [artifactId: "${pom.artifactId}", \
               groupId: "${pom.groupId}", \
               packaging: "${pom.packaging}", \
               version: "${pom.version}"]]]
            }
        }       
        
    }
}
