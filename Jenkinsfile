pipeline {
  agent any
  stages {
    stage('check') {
      steps {
        sh '''                            echo "CF Login..."
                            cf api $IBM_CLOUD_API
                            cf login -u $IBM_CLOUD_DEVOPS_CREDS_USR -p $IBM_CLOUD_DEVOPS_CREDS_PSW -o $IBM_CLOUD_DEVOPS_ORG -s $IBM_CLOUD_SPACE
                            
                            export APP_STATUS=$(cf app datadictionary | grep \'requested state:\' | awk \'{print $3}\')
                            echo $APP_STATUS
                            if [ "$APP_STATUS"="stopped" ]; then
                                exit 1
                            fi'''
      }
    }
  }
}