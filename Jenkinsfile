pipeline {
    agent { label 'jenkins-agent' }
    tools {
        jdk 'java17'
        maven 'Maven3'
    }
    stages{
        stage("cleanup workspace"){
            steps {
                cleanWs()
            }
        }

        stage("checkout for SCM"){
            steps {
                git branch:'main', credentialsId:'github', url:'https://github.com/bipulprasai-official/java-resister-app'
            }
        }

        stage("Build Application"){
            steps { 
                sh "mvn clean package"
            }
        }

        stage("Test Application"){
            steps {
                sh "mvn test"
            }
        }

        stage("Sonarqube Analysis"){
            steps {
                script {
                    withSonarQubeEnv(credentialsId:'jenkins-sonarqube-token'){
                        sh "mvn sonar:sonar"
                    }
                }
            }
        }

        

    }	
}
