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
                def version = sh script: 'mvn help:evaluate -Dexpression=project.version -q -DforceStdout', returnStdout
                echo 'versionw ${version}'
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
