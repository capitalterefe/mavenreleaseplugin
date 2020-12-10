node(){
  
    
    
    
   // def xml = "https://repo.adobe.com/nexus/content/groups/public/ant/ant/maven-metadata.xml".toURL().text
 
  println "metadata"
 //   println root['@metadata']
   
 //     println "metadata versioing"
 //   println metadata.versioning
    
  //  println root['@versioning']
 //  println root.parent().text
    
 //  print root.metadata.versioning.versions.version.takeRight(5).collect({it.text()}).reverse()
    
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
                    
                    def xml = "https://repo.adobe.com/nexus/content/groups/public/ant/ant/maven-metadata.xml".toURL().text
                      echo xml
    def colors = new XmlSlurper().parseText(xml)
                  //echo colors
    echo "First Color: ${colors.versioning[0]}" //works fine
   echo "First Color: ${colors.versioning[0].versions[0]['@version'][0]}" 
       echo "First Color: ${colors.versioning[0].versions[0]['@version'][1]}" 

                    
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
