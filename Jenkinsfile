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
               nexusArtifactUploader artifacts: [[artifactId: 'VinayDevOpsLab', classifier: '', file: 'target/VinayDevOpsLab-0.0.8-SNAPSHOT.war', type: 'war']], credentialsId: 'admin', groupId: 'com.vinaysdevopslab', nexusUrl: '35.168.112.177:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'VinayDevOpsLab-SNAPSHOT', version: '0.0.8-SNAPSHOT'
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
