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
               nexusArtifactUploader artifacts: [[artifactId: 'VinayDevOpsLab', classifier: '', file: 'target/VinayDevOpsLab-0.0.9-SNAPSHOT.war', type: 'war']], credentialsId: 'Nexus_credentials', groupId: 'com.vinaysdevopslab', nexusUrl: '3.87.209.39:8081', nexusVersion: 'nexus3', protocol: 'https', repository: 'VinayDevOpsLab-SNAPSHOT', version: '0.0.9-SNAPSHOT'
            }
        }
        
        //stage4: Deploying
        stage ('Deploy'){
            steps{
              sshPublisher(publishers: 
                           [sshPublisherDesc
                            (configName: 'Ansible_controller',
                             transfers: [
                                sshTransfer(
                                        cleanRemote:false,
                                        execCommand: 'ansible-playbook /opt/playbooks/downloaddeploy.yaml -i /opt/playbooks/hosts',
                                        execTimeout: 120000
                                )
                             ],
                             usePromotionTimestamp: false,
                             useWorkspaceInPromotion: false,
                             verbose: false)
                            ])
            }
        }

    }
}
