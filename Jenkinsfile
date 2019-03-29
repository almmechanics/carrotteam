agentName = "ubuntu"


pipeline {

    agent { label agentName }
   
    stages {
        stage('Test') {
            steps {
                sh 'echo hello'
            }
        }
    }   
}
