pipeline{
    agent{ docker 'maven:3.5-alpine'}
    stages{
        stage('SCM'){
            steps{
                git 'https://github.com/vinaygwd/spring-petclinic.git'
            }
        }
        stage('Build'){
            steps{
                sh 'package'
                junit '**/target/surefire-reports/TEST-*.xml'
            }
        }
    }
}
