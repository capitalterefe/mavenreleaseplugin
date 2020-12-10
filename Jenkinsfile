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
                    
                        echo 'Building..'
                        echo "version ${VERSION}"
                        echo "version ${ARTIFACT}"
                        echo "version ${GROUP}"

                    def host="https://msnexus.xxx.com"
                    def groupId="com.xxx.cd".replaceAll("\\.", "/")
                    def artifactId="common-log"
                    def nexus_url="${host}/repository/public/${groupId}/${artifactId}/maven-metadata.xml"
                    def nexus_url2="https://repo.adobe.com/nexus/content/groups/public/ant/ant/maven-metadata.xml"
                    def metadata = new XmlParser().parseText(nexus_url2)
                   //metadatastr = metadata.versioning.versions.version.takeRight(5).collect({it.text()}).reverse()
                    echo "metada: ${nexus_url2}"

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
