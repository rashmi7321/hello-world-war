pipeline {

	agent any
	environment {
		MVN_HOME = '/opt/maven'
	}
			stages{
   
		stage('checkout') {
				steps {
					checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'github', url: 'https://github.com/rashmi7321/hello-world-war.git']]])
				}
          
			}
			stage('Build') {
				steps { 
					sh "mvn clean install"
				}
			}

			stage("publish to nexus") {
				steps {
def pom = readMavenPom file: 'pom.xml'
 nexusPublisher nexusInstanceId: 'nexusrepo', \
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
