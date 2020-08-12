pipeline {
    agent any
    stages {
       
        stage('Deploy CloudHub') {
            steps {
                sh 'mvn deploy -DskipTests -DmuleDeploy -Dmule.version=4.2.2 -Danypoint.username=tonsallimule -Danypoint.password=Rukmini@01 -Danypoint.environment=Sandbox -e'
            }
        }
    }
    
}
