agentName = "cucumberteam"


pipeline {

    agent { label agentName }
   
    stages {
        stage('Login') {
            steps {
                sh 'az login --identity '
            }
        }
        stage('Resource Creation') {
            steps {
                sh 'az storage account create --name cucumber$(date +%s) --resource-group rg_cucumber --sku Standard_LRS --location westeurope'
            }
        }
        stage('List Resources') {
            steps {
                sh 'az resource list | jq ".[].name"'
            }
        }
        stage('Logout') {
            steps {
                sh 'az logout'
            }
        }
    }   
}
