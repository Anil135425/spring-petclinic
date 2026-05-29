pipeline{
    agent{label 'SPC'}
    triggers{
        pollSCM('* * * * *')
    }
    stages{
        stage('git checkout'){
            steps{
                git url:'https://github.com/spring-projects/spring-petclinic.git',
                branch:'main'
            }
        }
        stage('scan'){
            steps{
                withCredentials([string(credentialsId: 'sonar_id', variable: 'SONAR_TOKEN')]) {
                withSonarQubeEnv('sonar_qube') {
                sh """"mvn clean verify sonar:sonar \
                       -Dsonar.projectKey=Anil135425_springspetic \
                       -Dsonar.organization=Anil135425 \
                       -Dsonar.host.url=https://sonarcloud.io/ \
                       -Dsonar.login=$SONAR_TOKEN"""
                }
                }
            }
        }
    
    }
}
