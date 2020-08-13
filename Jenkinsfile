pipeline {
    agent any
    stages {
       
        stage('Deploy CloudHub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'anypoint', passwordVariable:'pass', usernameVariable:'user')]){ 
                sh 'mvn clean package deploy  -DskipTests=true -Dmule.version=4.2.2 -Danypoint.environment=Sandbox -Danypoint.username=$user -Danypoint.password=$pass -X'
                }
                
                }
        }
    }
    
}
