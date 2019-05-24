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
                sh 'mvn clean package'
                junit '**/target/surefire-reports/TEST-*.xml'
                archiveArtifacts artifacts: 'targets/*.jar' , fingerprint: true
            }
        }
        stage('Deploy'){
            steps{
                input 'Do i need to deploy?'
                sh 'scp target/*.jar jenkins@10.160.0.4:/opt/pet'
                sh "ssh jenkins@10.160.0.4 'nohup java -jar /opt/pet/spring-petclinic-2.1.0.BUILD-SNAPSHOT.jar &'"
            }
        }
    }
}
