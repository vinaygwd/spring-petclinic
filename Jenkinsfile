pipeline{
    agent { label 'java'}
    stages{
        stage('SCM'){
            steps{
                git 'https://github.com/vinaygwd/spring-petclinic.git'
            }
        }
        stage('Build'){
            agent{ docker 'maven:3.5-alpine'}
            steps{
                sh 'mvn clean package'
                junit '**/target/surefire-reports/TEST-*.xml'
                archiveArtifacts artifacts: 'target/*.jar' , fingerprint: true
            }
        }
        stage('Deploy'){
            steps{
                input 'Do i need to deploy?'
                sh 'nohup java -jar /opt/pet/spring-petclinic-2.1.0.BUILD-SNAPSHOT.jar &'
            }
        }
    }
}
