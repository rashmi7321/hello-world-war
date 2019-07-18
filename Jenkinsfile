stage("mvn build and push") {
                    sh """
                    mkdir -p /root/.m2/
                    cp -rf settings.xml settings-security.xml /root/.m2/
                    mvn deploy -DskipTests=true
                    """
        }
