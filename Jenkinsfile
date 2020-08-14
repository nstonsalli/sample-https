pipeline {
    agent any
    stages {
        stage('Deploy CloudHub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'anypoint', passwordVariable:'pass', usernameVariable:'user')]){ 
                bat "mvn clean package deploy -DskipTests=true -Dmule.version=4.2.2 -Dmule.environment=Sandbox -Danypoint.username=$user -Danypoint.password=$pass -X"
                }
                
                }
        }
    }
    
}
