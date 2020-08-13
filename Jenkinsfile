pipeline {
    agent any
    mvnHome = tool 'M3'
    stages {
       
        stage('Deploy CloudHub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'anypoint', passwordVariable:'pass', usernameVariable:'user')]){ 
                sh "'${mvnHome}/bin/mvn' clean package deploy  -DskipTests=true -Dmule.version=4.2.2 -Danypoint.environment=Sandbox -Danypoint.username=$user -Danypoint.password=$pass -X"
                }
                
                }
        }
    }
    
}
