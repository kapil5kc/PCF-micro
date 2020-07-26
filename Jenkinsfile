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

                    sh 'cf login -a https://api.sys.parivartandev1.com -u kapil.chauhan1@wipro.com -p changeme'
                    sh 'cf push'
            }
        }
    }
}