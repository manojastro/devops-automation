pipeline {
    agent any
    stages{
        stage('Build Maven'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Java-Techie-jt/devops-automation']]])
                sh 'mvn clean install'
            }
        }
        stage('Build docker image'){
            steps{
                script{
                    sh 'docker build -t manojastro/devops-integration .'
                }
            }
        }
        stage('Push image') {
        withDockerRegistry([ credentialsId: "manojastro", url: "" ]) {
        dockerImage.push()

}
                }
            }
        }
        
 
