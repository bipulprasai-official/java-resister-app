pipeline {
    agent { label 'Jenkins-Agent' }
    tools {
        jdk 'Java17'
        maven 'maven3'
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

   
        

    }	
}
