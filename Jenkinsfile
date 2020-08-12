pipeline {
    agent any
    stages {
       
        stage('Deploy CloudHub') {
            environment {
                ANYPOINT_CREDENTIALS = credentials('anypoint.credentials')
            }
            steps {
                sh 'echo $PATH'
                slackSend (color: '#FFFF00', message: "${env.ENV} > Deploying to Cloudhub: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (<${env.BUILD_URL}|Open>)")
                sh 'mvn deploy -DskipTests -DmuleDeploy -Dmule.version=4.2.2 -Danypoint.username=${ANYPOINT_CREDENTIALS_USR} -Danypoint.password=${ANYPOINT_CREDENTIALS_PSW} -e'
            }
        }
    }
    
}
