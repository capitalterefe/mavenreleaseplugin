def xml = "https://repository.jboss.org/nexus/service/local/lucene/search?g=jboss&a=jboss-j2ee&r=releases&p=jar".toURL().text
def root = new XmlParser().parseText(xml)
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
               
                script{
                    
                    echo "${root}"
                    echo root
                 root.versioning.versions.version.takeRight(5).collect({it.text()}).reverse()
                    
                }
                
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
