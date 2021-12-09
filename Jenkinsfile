pipeline{
  //Directives
    agent any
    tools{
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
                nexusArtifactUploader artifacts: [[artifactId: 'VinayDevOpsLab', classifier: '', file: 'target/com.vinaysdevopslab-0.0.9-SNAPSHOT.war', type: 'war']], credentialsId: '65996900-02b7-49ed-94b4-386c19fbd0d5', groupId: 'com.vinaysdevopslab', nexusUrl: '44.200.222.66:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'GauravDevOpsLab-SNAPSHOT', version: '0.0.9-SNAPSHOT'
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
