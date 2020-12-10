pipeline {
    agent any
     
    environment {
    //Use Pipeline Utility Steps plugin to read information from pom.xml into env variables
    ARTIFACT = readMavenPom().getArtifactId()
    VERSION = readMavenPom().getVersion()
    GROUP = readMavenPom().getGroupId()
    }


    stages {
                     
        
        
        stage('Build') {
            steps {
               
                sh(script:
                    
                    def xml = "https://repository.jboss.org/nexus/service/local/lucene/search?g=jboss&a=jboss-j2ee&r=releases&p=jar".toURL().text
                    def root = new XmlParser().parseText(xml)
                    return root.data.artifact.collect {"${it.groupId.text()}:${it.artifactId.text()}:${it.version.text()}"}
                     
                    )
                }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
    
}
