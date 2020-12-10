node(){
    String xml = """
<dogs>
 <dog type="Beagle" sound="howl"/>
 <dog type="Labrador" sound="woof"/>
</dogs>"""

XmlParser parser = new XmlParser()
def dogs = parser.parseText (xml)

dogs.dog.each { dog ->
    println("${dog.'@type'} sounds like ${dog.'@sound'}");
}
    
    
    
    def xml = "https://repo.adobe.com/nexus/content/groups/public/ant/ant/maven-metadata.xml".toURL().text
    println xml
   def root = new XmlParser().parseText(xml)
    println 'root print'
    println root
 
   println "metadata"
    println root['@metadata']
   
      println "metadata versioing"
    println metadata.versioning
    
    println root['@versioning']
   println root.parent().text
    
   print root.metadata.versioning.versions.version.takeRight(5).collect({it.text()}).reverse()
    
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
