pipeline {
    //Directives
    agent any
    tools {
        maven 'M2_HOME'
    }

    stages {
        // Specify various stage with in stages

        // stage 1. Build
        stage ('Build'){
            steps {
                sh 'mvn clean install package'
            }
        }

        // Stage2 : Testing
        stage ('Test'){
            steps {
                echo ' testing......'
            }
        }

        stage  ('Deployment to nexus repo'){
            steps {
                nexusArtifactUploader artifacts: [[artifactId: 'VinayDevOpsLab', classifier: '', file: 'target/VinayDevOpsLab-1.0.0.war', type: 'war']], credentialsId: 'nexus-cred', groupId: 'com.vinaysdevopslab', nexusUrl: '3.9.191.44:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'Test-repo', version: '1.0.0'
            }
        }        
        // Stage3 : Publish the source code to Sonarqube
        // stage ('Sonarqube Analysis'){
        //     steps {
        //         echo ' Source code published to Sonarqube for SCA......'
        //         withSonarQubeEnv('sonarqube'){ // You can override the credential to be used
        //              sh 'mvn sonar:sonar'
        //         }
        //     }
        // }
    }
}
