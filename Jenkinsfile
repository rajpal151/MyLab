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
                scrpt{
                    def NexusRepo = version.endWith("SNAPSHOT") ? "VinayDevOpsLab-SNAPSHOT" : "VinayDevOpsLab-RELEASE"
                nexusArtifactUploader artifacts:
                [[artifactId: 'VinayDevOpsLab', 
                classifier: '', 
                file: "target/${ArtifactId}-${Version}.war", 
                type: 'war']], 
                credentialsId: 'b50c9160-deca-4804-b0ed-ddd4a01f1ea0', 
                groupId: 'com.vinaysdevopslab', 
                nexusUrl: '3.238.123.71:8081', 
                nexusVersion: 'nexus3', 
                protocol: 'http', 
                repository: "${NexusRepo}", 
                version: "${Version}"
                }
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
