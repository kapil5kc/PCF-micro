pipeline {

    agent any

    stages {

        stage ('Build') {
            steps {
                withMaven(maven: 'maven_3_2_2') {
                    sh 'mvn clean package'
                }
            }
        }

        stage ('Deploy') {
            steps {

                withCredentials([[$class          : 'UsernamePasswordMultiBinding',
                                  credentialsId   : 'PCF_LOGIN',
                                  usernameVariable: 'USERNAME',
                                  passwordVariable: 'PASSWORD']]) {

                    sh 'cf login -a https://api.sys.parivartandev1.com -u $USERNAME -p $PASSWORD'
                    sh 'cf push'
                }
            }

        }

    }

}