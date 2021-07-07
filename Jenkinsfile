pipeline {
    agent any
    tools {
        maven 'MAVEN'
    }
    
    stages{
        stage('Build'){
            steps{
                 sh script: 'mvn clean package'
           
            }
        }
        stage('Upload War To Nexus'){
            steps{
                

                    nexusArtifactUploader artifacts: [
                        [
                            artifactId: 'simple-app', 
                            classifier: '', 
                            file: 'target/simple-app-1.0.0.war', 
                            type: 'war'
                        ]
                    ],
                            credentialsId: 'nexus3',
                            groupId: 'in.javahome',
                            nexusUrl: '172.31.4.229:8081',
                            nexusVersion: 'nexus3',
                            protocol: 'http',
                            repository: 'simpleapp-release',
                            version: '1.0.0'
                  
            }
        }
    }
}