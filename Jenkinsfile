pipeline {
    agent any
    environment {
         NEXUS_USER    = 'admin'
        NEXUS_PASSWORD = 'admin'
        NEXUS_VERSION = 'nexus3'
        NEXUS_PROTOCOL = 'http'
        NEXUS_URL = 'http://44.220.134.169:8081/repository/myownproject2/'
        GROUP_ID = 'com.example'
        REPOSITORY = 'myownproject2'
        CREDENTIALS_ID = 'nexus_cread'
        VERSION = '1.0-SNAPSHOT' 
        ARTIFACT_ID = 'basic-webpage'
     }

    stages {
        stage('Build') {
            steps {
                sh 'mvn package'
            }
        }
        stage('continous upload') {
            steps {
                nexusArtifactUploader(
                    nexusVersion: 'NEXUS_VERSION',
                    protocol: 'http',
                    nexusUrl: "${NEXUS_URL}",
                    groupId: "${GROUP_ID}",     
                    version: "${VERSION}",
                    repository: "${REPOSITORY}",
                    credentialsId: "${CREDENTIALS_ID}",
                    artifacts: [
                        [
                            artifactId: "${ARTIFACT_ID}",
                            classifier: '',
                            file: 'target/basic-webpage-1.0-SNAPSHOT.war',
                            type: 'war'
                        ]
                    ]
                )

            }
        }   
    }
}