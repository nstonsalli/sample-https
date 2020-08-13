pipeline {
    agent any
    stages {
       
        stage('Deploy CloudHub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'anypoint', passwordVariable: 'anypoint-pass', usernameVariable: 'anypoint-user')]){ 
                bat 'mvn clean package deploy  -DskipTests=true -DmuleDeploy -Dmule.version=4.2.2 -Danypoint.environment=Sandbox -Danypoint.username=$anypoint-user -Danypoint.password=$anypoint-pass'
                }
                
                }
        }
    }
    
}
