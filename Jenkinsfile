pipeline{
    agent{label 'SPCJAVA'}
    triggers{
        pollSCM('* * * * *')
    }
    stages{
        stage('git checkout'){
            steps{
                git url:'https://github.com/Anil135425/spring-petclinic.git',
                branch:'main'
            }
        }
        stage('scan'){
            steps{
                withSonarQubeEnv('sonar_qube') {
                sh 'mvn package sonar:sonar'
                }
            }
        }
    }
}