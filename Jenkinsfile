pipeline {
    agent any
    stages {
       
        stage('Deploy CloudHub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'anypoint', passwordVariable: 'git-pass', usernameVariable: 'git-user')]){
                bat 'mvn clean install -DskipTests -DmuleDeploy -Dmule.version=4.2.2 -Danypoint.username=$git-user -Danypoint.password=$git-pass -Danypoint.environment=Sandbox -e'
                }
                
                }
        }
    }
    
}
