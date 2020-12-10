pipeline {
    agent any
     
    environment {
    //Use Pipeline Utility Steps plugin to read information from pom.xml into env variables
    ARTIFACT = readMavenPom().getArtifactId()
    VERSION = readMavenPom().getVersion()
    GROUP = readMavenPom().getGroupId()
    }

def getProjectVersion(){
  def file = readFile('pom.xml')
  def project = new XmlSlurper().parseText(file)
  return project.version.text()
}

def getReleaseVersion(String artifact) {
  def modelMetaData = new XmlSlurper().parse("https://oss.sonatype.org/content/repositories/releases/${artifact}/maven-metadata.xml")
  def version = modelMetaData.versioning.release.text()
  return version
}
    stages {
                     
        
        
        stage('Build') {
            steps {
               
                script{
                    versions=getProjectVersion()
                    echo 'versioning $versions'
                     
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
