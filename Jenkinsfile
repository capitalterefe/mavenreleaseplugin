


pipeline {
    agent any
     
    environment {
        //https://repo.adobe.com/nexus/service/local/lucene/search?g=ant&a=ant
    //Use Pipeline Utility Steps plugin to read information from pom.xml into env variables
    ARTIFACT = readMavenPom().getArtifactId()
    VERSION = readMavenPom().getVersion()
    GROUP = readMavenPom().getGroupId()
    }


    stages {
                     
        
        
        stage('Build') {
            steps {
               
                script{
                        def releaseScope = ["Angular", "Groovy", "Java"];
                        def releaseScopeChoices = ''
                        releaseScope.each {
                            releaseScopeChoices += it + '\\n'
                        }
                        println releaseScopeChoices
                        parameters: [choice(name: 'RELEASE_SCOPE', choices: "${releaseScopeChoices}", description: 'What is the release scope?')]

                    
                    
                  def metad = "http://maven.wso2.org/nexus/content/repositories/snapshots/org/wso2/is/wso2is/maven-metadata.xml"
                    def versions = sh(script: "curl -s ${metad} | grep version", returnStdout: true).trim()
//                   def versions = sh(script: "curl -s ${metad} | grep '<version>.*</version>' | sed -e 's#\(.*\)\(<latest>\)\(.*\)\(</latest>\)\(.*\)#\3#g'", returnStdout: true)
                    println versions
                    
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


