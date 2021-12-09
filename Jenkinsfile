pipeline{
    //Directives
    agent any
    tools {
        maven 'maven'
    }
    stages{
        //stage1: Build
        stage ('Build'){
            steps{
                sh 'mvn clean install package'
            }
        }

        //stage2: Testing
        stage ('Test'){
            steps
            {
                echo 'testing.......'
            }
        }

        //stage3: Publishing Artifacts to nexus
        stage ('Publish to nexus'){
            steps{
                nexusArtifactUploader artifacts: [[artifactId: 'VinayDevOpsLab', classifier: '', file: 'target/VinaysDevOpsLab-0.0.9-SNAPSHOT.war', type: 'war']], credentialsId: 'b50c9160-deca-4804-b0ed-ddd4a01f1ea0', groupId: 'com.vinaysdevopslab', nexusUrl: '3.238.123.71:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'VinaysDevOpsLab-SNAPSHOT', version: '0.0.9-SNAPSHOT'
                }
        }

        //stage4: Deploying
        stage ('Deploy'){
            steps{
                echo 'deploying.......'
            }
        }

    }
}
