@NonCPS
def servers(xml) {
    new XmlParser().parseText(xml).Config.Servers.Server.collect{it.@Name}
}

node{
    def paramxml="""
                    
                    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
                              <AS Name="123">
                                  <Config Name="Configuration1">
                                      <Servers>
                                          <Server Name="server1"/>
                                          <Server Name="server2"/>
                                          <Server Name="server3"/>
                                          <Server Name="server4"/>
                                       </Servers>
                                  </Config>
                              </AS>
                    
                    """
                  
    println servers(paramxml)
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
                  
                    print hello
                  
                    
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


