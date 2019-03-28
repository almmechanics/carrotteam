pipeline {
    agent {
    node {
            label 'ubuntu'
         }
    }
    stages {
        stage('Login') {
            steps {
                withCredentials([azureServicePrincipal('AzureServicePrincipal')]) {
                    sh 'az login --service-principal -u $AZURE_CLIENT_ID -p $AZURE_CLIENT_SECRET -t $AZURE_TENANT_ID'
                }
            }
        }
        stage('Resource Creation') {
            steps {
                withCredentials([azureServicePrincipal('AzureServicePrincipal')]) {
                    sh 'az storage account create --name cucumber$(date +%s) --resource-group rg_cucumber --sku Standard_LRS --location westeurope'
                }
            }
        }
        stage('List Resources') {
            steps {
                withCredentials([azureServicePrincipal('AzureServicePrincipal')]) {
                    sh 'az resource list | jq ".[].name"'
                }
            }
        }
        stage('Logout') {
            steps {
                withCredentials([azureServicePrincipal('AzureServicePrincipal')]) {
                    sh 'az logout'
                }
            }
        }
    }
}
