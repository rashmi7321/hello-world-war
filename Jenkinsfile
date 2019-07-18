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
					sh "mvn deploy -DskipTests=true"
				}
			}

			stage('UploadToNexus'){
				steps {
					nexusPublisher nexusInstanceId: 'nexusrepo', nexusRepositoryId: 'sample', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: 'target/ROOT.war']], mavenCoordinate: [artifactId: 'sample', groupId: 'maven', packaging: 'war', version: '$BUILD_NUMBER']]]
				}
			}
    }
}
