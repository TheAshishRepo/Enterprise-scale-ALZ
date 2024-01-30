pipeline {
    agent any 

    environment {
        AZURE_RG_NAME = 'Demo-RG'
        AZURE_LOCATION = 'EastUS'
        AZURE_TEMPLATE_FILE = '${AZURE_TEMPLATE_FILE}'
        AZURE_PARAMETERS_FILE = '${AZURE_PARAMETERS_FILE}'
        //AZURE_DEPLOYMENT_NAME = 'Demo'
        AZURE_CLIENT_ID = '${AZURE_CLIENT_ID}'
        AZURE_CLIENT_SECRET = '${AZURE_CLIENT_SECRET}'
        AZURE_TENANT_ID = '${AZURE_TENANT_ID}'
        AZURE_SUBSCRIPTION_ID = 'f0c38c3b-77fd-4828-bb35-c7c22eecb247'

    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    // Checkout your source code repository
                    checkout scm
                }
            }
        }

        
    
        stage('Deploy CAF-Landing Zone') {
            steps {
                script {

                     // Run multiple commands using a script block
                    powershell '''
                        $ESLZPrefix = "CAF-LZ"
                        $Location = "EastUS"
                        $DeploymentName = "EntScale"
                        $TenantRootGroupId = "${(Get-AzTenant).Id}"
                        $ManagementSubscriptionId = "top_level_mgmt_group"
                        $ConnectivitySubscriptionId = "CAF_connectivity_SID"
                        $ConnectivityAddressPrefix = "10.0.0.20/24"
                        $IdentitySubscriptionId = "CAF_Identity_SID"
                        $SecurityContactEmailAddress = "webashu@gmail.com"
                        $CorpConnectedLandingZoneSubscriptionId = "CAF_LZ_SID" 
                        $OnlineLandingZoneSubscriptionId = "ONL_LZ_SID"
                    '''
                    
                    // Run a PowerShell script from a file
                    powershell returnStatus: true, script: './var/lib/jenkins/workspace/Enterprise-scale-Landing-Zone/src/scripts/CAF-landingZone.ps1'
                    
                   
                }
            }
        }
    


}
}
