pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                def pom = readMavenPom file: 'pom.xml'
                echo pom.version
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
