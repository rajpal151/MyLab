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
                nexusArtifactUploader artifacts: [[artifactId: 'VinayDevOpsLab', classifier: '', file: 'target/VinayDevOpsLab-0.0.9-SNAPSHOT.war', type: 'war']], credentialsId: '62b984ce-5791-4a8b-982a-c34f99ec2af9', groupId: 'com.vinaysdevopslab', nexusUrl: '3.236.217.132:8080', nexusVersion: 'nexus3', protocol: 'http', repository: 'VinayDevOpsLab-SNAPSHOT', version: '0.0.9-SNAPSHOT'
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
