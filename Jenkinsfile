


pipeline {
    agent any
   
    parameters {
                        choice(
                            name: 'myParameter',
                            choices: "a\nb",
                            description: 'interesting stuff' )
                      }   
 
    
   
    
    
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
                       
                    
            def versions = sh(script: "curl -s https://repo1.maven.org/maven2/org/brutusin/wava/maven-metadata.xml | grep -Po '(?<=<version>)([0-9\\.]+(-SNAPSHOT)?)' | sort --version-sort -r | head -n 3", returnStdout: true).trim().split("\r?\n")
            int top = versions.size()
            LATEST = "${versions[top-3]}"
            PREVIOUS = "${versions[top-2]}"        
            OLD = "${versions[top-1]}"
                
            println("$versions")


            deploy_version= input message: 'select version to deploy : ', 
            parameters: [ choice (name: 'Environment to deploy to' , choices: "${LATEST}\n${PREVIOUS}\n${OLD}", description: 'choose env')]
            echo " The environment is ${params.myParameter}"
            echo " The environment is ${deploy_version}"
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


