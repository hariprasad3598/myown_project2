pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'mvn package'
            }
        }
        stage('continous upload') {
            steps {
                 nexusArtifactUploader artifacts: [[artifactId: 'basic-webpage', classifier: '', file: 'target/basic-webpage-1.0-SNAPSHOT.war', type: 'war']], credentialsId: 'nexus_cread', groupId: 'com.example', nexusUrl: '3.92.52.140:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'myownproject2', version: '1.0-SNAPSHOT'    
            
            }
        }   
    }
}