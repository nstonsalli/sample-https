pipeline {
    agent any
    stages {
       
        stage('Deploy CloudHub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'anypoint', passwordVariable: 'git-pass', usernameVariable: 'git-user')]){ 
                bat 'mvn clean install -DskipTests=true -DmuleDeploy -Dmule.version=4.2.2 -Dmule.environment=Sandbox -Danypoint.username=$git-user -Danypoint.password=$git-pass'
                }
                
                }
        }
    }
    
}
