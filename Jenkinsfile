pipeline {
    agent any
     
    environment {
    //Use Pipeline Utility Steps plugin to read information from pom.xml into env variables
    ARTIFACT = readMavenPom().getArtifactId()
    VERSION = readMavenPom().getVersion()
    GROUP = readMavenPom().getGroupId()
    }

    stages {
        
        
        def host="https://msnexus.xxx.com"
def groupId="com.xxx.cd".replaceAll("\\.", "/")
def artifactId="common-log"
def nexus_url="${host}/repository/public/${groupId}/${artifactId}/maven-metadata.xml"
def response=nexus_url.toURL().text
def metadata = new XmlParser().parseText(response)

metadata.versioning.versions.version.takeRight(5).collect({it.text()}).reverse()
        stage('Build') {
            steps {
               
                echo 'Building..'
                echo "version ${VERSION}"
                echo "version ${ARTIFACT}"
                echo "version ${GROUP}"
                
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
