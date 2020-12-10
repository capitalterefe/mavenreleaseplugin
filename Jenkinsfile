node(){
    def xml = "https://repo.adobe.com/nexus/content/groups/public/ant/ant/maven-metadata.xml".toURL().text
   def root = new XmlParser().parseText(xml)
   println root.text()
    println root['@versioning']
   println root.parent().text
    
   print root.versioning.versions.version.takeRight(5).collect({it.text()}).reverse()
    
}
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
                    
                    //echo "${root}"
                   
                   echo "hello builder"
                    
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
