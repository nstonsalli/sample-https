pipeline {
    agent any
    stages {
        stage('Deploy CloudHub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'anypoint', passwordVariable:'pass', usernameVariable:'user')]){ 
                bat "mvn clean package deploy -DskipTests=true -Danypoint.environment=Sandbox -Dmule.version=4.2.2 -Danypoint.username=$user"
                }
                
                }
        }
    }
    
}
