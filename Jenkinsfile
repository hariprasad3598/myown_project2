pipeline {
    agent any
    environment {
         NEXUS_USER    = 'admin'
        NEXUS-PASSWORD = 'admin'
        NEXUS_VERSION = 'nexus3'
        NEXUS_PROTOCOL = 'http'
        NEXUS_URL = '107.22.11.112:8081'
        GROUP_ID = 'com.example'
        REPOSITORY = 'myownproject2'
        CREDENTIALS_ID = 'nexus_cred'
        VERSION = '1.0-SNAPSHOT' 
        ARTIFACT_ID = 'Basic Web Page'
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
                    nexusVersion: 'nexus3',
                    protocol: 'http',
                    nexusUrl: "${NEXUS_URL}",
                    groupId: "${GROUP_ID}"     
                    version: "${GROUP_ID}",,
                    repository: "${NEXUS_REPOSITORY}",
                    credentialsId: "${CREDENTIALS_ID}",
                    artifacts: [
                        [
                            artifactId: "${ARTIFACT_ID}",
                            classifier: '',
                            file: "${ARTIFACT_ID}-${VERSION}.war",
                            type: 'war'
                        ]
                    ]
                )

            }
        }   
    }
}