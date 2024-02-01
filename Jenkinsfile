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
                        az login --service-principal -u 7f707d6e-9b20-4963-ab1d-11383794c758 -p Zr18Q~QCK4uP6fVW5D4KermCwnCkRtjqr2E62b6Y --tenant d0e16214-52b0-43f5-879b-faf4fc79ccf3
                        az account set --subscription ca751fb4-e672-40d0-9d86-91827c006eab
                        $ESLZPrefix = "CAF-LZ"
                        $Location = "EastUS"
                        $DeploymentName = "EntScale"
                        $TenantRootGroupId = "d0e16214-52b0-43f5-879b-faf4fc79ccf3"
                        $ManagementSubscriptionId = "1860edbc-2aab-4083-aad2-ff6fa68ddd79"
                        $ConnectivitySubscriptionId = "ca751fb4-e672-40d0-9d86-91827c006eab"
                        $ConnectivityAddressPrefix = "10.0.0.20/24"
                        $IdentitySubscriptionId = "58755c69-412e-4307-a49d-94f3d8074724"
                        $SecurityContactEmailAddress = "webashu@gmail.com"
                        $CorpConnectedLandingZoneSubscriptionId = "xxxxxxx" 
                        $OnlineLandingZoneSubscriptionId = "xxxxx"
                        .\\CAF-landingZone.ps1 
                    '''

                    // Run a PowerShell script from a file
                    //powershell returnStatus: true, script: '/var/lib/jenkins/workspace/Enterprise-scale-Landing-Zone/src/scripts/CAF-landingZone.ps1'
                    //echo "hello world"
                    //powershell returnStatus: true, script: '.\\CAF-landingZone.ps1'
                    
                    
                   
                }
            }
        }    
    }
}
