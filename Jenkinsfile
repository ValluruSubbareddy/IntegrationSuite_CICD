@Library('piper-lib-os') _
 
pipeline{
	agent {
		node {
		label 'SAP_BTP_uxuselkgcp4021'
		}
	}
	options {
	disableConcurrentBuilds()
	}
 
     stages{
    		stage('init') {
					steps{  
					   script{
    				   deleteDir()
						sh 'cd $WORKSPACE'
						sh 'pwd'
						sh 'alias'
					   setupCommonPipelineEnvironment script: this
					   }}
				}
          stage('uploadIntegrationArtifact Command') {
               integrationArtifactUpload script: this
                }		
          stage('deployIntegrationArtifact Command') {
               integrationArtifactDeploy script: this
                }
}
   post{
				always{
				  script {                                    
					  	// Cleanup workspace
						echo "Cleanup"
						cleanWs()
					}}}
 
}
