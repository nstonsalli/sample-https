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
    post {
        failure {
            slackSend color: 'danger', message: "@here \n${env.ENV} > FAILED ${env.JOB_NAME} [${env.BUILD_NUMBER}] (<${env.BUILD_URL}|Open>)"
        }
        success {
            slackSend color: 'good', message: "${env.ENV} > SUCCESS ${env.JOB_NAME} [${env.BUILD_NUMBER}] (<${env.BUILD_URL}|Open>)"
        }
    }
}

void setEnvironmentVars(String envParam) {
    if (envParam != null){
        echo "DEBUG: envParam=$envParam"

        env.CLOUDHUB_ENVIRONMENT = envParam

        if (env.CLOUDHUB_ENVIRONMENT == "Development") {
            env.ENV = "dev"
        } else if (env.CLOUDHUB_ENVIRONMENT == "Beta") {
            env.ENV = "beta"
        } else if (env.CLOUDHUB_ENVIRONMENT == "Production") {
            env.ENV = "prod"
        }
    } else {
        env.CLOUDHUB_ENVIRONMENT = "Development"
        env.ENV = "dev"
    }

    withCredentials([usernamePassword(credentialsId: 'anypoint.client.' + env.ENV, passwordVariable: 'ANYPOINT_CLIENT_SECRET', usernameVariable: 'ANYPOINT_CLIENT_ID')]) {
        env.ANYPOINT_CLIENT_ID = "$ANYPOINT_CLIENT_ID"
        env.ANYPOINT_CLIENT_SECRET = "$ANYPOINT_CLIENT_SECRET"
    }

    withCredentials([usernamePassword(credentialsId: 'logger', passwordVariable: 'LOGGER_TOKEN', usernameVariable: 'LOGGER_URL')]) {
        env.LOGGER_URL = "$LOGGER_URL"
        env.LOGGER_TOKEN = "$LOGGER_TOKEN"
    }

    withCredentials([string(credentialsId: 'masterKey.' + env.ENV, variable: 'MASTER_KEY')]) {
        env.MASTER_KEY = "$MASTER_KEY"
    }

    echo "DEBUG: setEnvironment: CLOUDHUB_ENVIRONMENT: ${env.CLOUDHUB_ENVIRONMENT}"
    echo "DEBUG: setEnvironment: ENV: ${env.ENV}"
    echo "DEBUG: setEnvironment: PATH: ${env.PATH}"
}
