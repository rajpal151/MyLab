pipeline{
    //Directives
    agent any
    tools {
        maven 'maven'
    }

    environment{
        ArtifactId = readMavenPom().getArtifactId();
        Version = readMavenPom().getVersion();
        Name = readMavenPom().getName();
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
                nexusArtifactUploader artifacts: [[artifactId: 'VinayDevOpsLab', classifier: '', file: 'target/VinaysDevOpsLab-0.0.9-SNAPSHOT.war', type: 'war']], credentialsId: '30fd22be-c229-4537-9d05-0b3c10632324', groupId: 'com.vinaysdevopslab', nexusUrl: '18.208.187.71:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'VinaysDevOpsLab-SNAPSHOT', version: '0.0.9-SNAPSHOT'
                }
        }

        //stage4: Print Imp Information
        stage ('Print Environment Variables'){
            steps{
                echo "Artifact Id is '{$ArtifactId}'"
                echo "Version is '{$Version}'"
                echo "GroupId is '{}'"
                echo "Name is '{$Name}'"
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
