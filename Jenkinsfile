
pipeline {
    agent any
    
   
   
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
        
        
    }
}
