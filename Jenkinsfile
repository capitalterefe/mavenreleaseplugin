


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
            VERSION_I = "${versions[top-2]}"
            VERSION_II = "${versions[top-1]}"
            VERSION_III = "${versions[top-0]}"        
            println("Version1: $VERSION_I \n Version11 $VERSION_II \n Version111 $VERSION_III ")


            deploy_version= input message: 'select version to deploy : ', 
            parameters: [ choice (name: 'Environment to deploy to' , choices: "${VERSION_I}\n${VERSION_II}\n${VERSION_II}", description: 'choose env')]
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


