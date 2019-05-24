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
            input 'Do i need to deploy?'
            echo "deploying"
        }
    }
}
