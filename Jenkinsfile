pipeline {
    agent any

    stages {
        stage('InitEB') {
            steps {
                  dir('eb'){
                       sh 'eb init hello-eb -k clave-lucatic -p"Docker running on 64bit Amazon Linux 2" --region eu-west-1'
                  }
            }
        }
        stage('CreateEB') {
            steps {
                withAWS(credentials: 'credenciales-aws', region: 'eu-west-1') {
                      dir('eb'){
                         sh 'eb create --elb-type application -c hello-eb -i t2.micro'
                      }                     
                }
            }
        }

    }
}

