pipeline{
    agent any
    
    environment{
        PATH = "/opt/maven3/bin:$PATH"
    }
    stages{
        stage("Git Checkout"){
            steps{
               git branch: 'main', credentialsId: '7d84fdc7-9cae-45ec-9d80-f34b643a51c6', url: 'https://github.com/sowmya1597/svvs-repo4.git'
            }
        }
        stage("Maven Build"){
            steps{
                sh "mvn clean package"
                sh "mv target/*.war target/myweb.war"
            }
        }
        stage("deploy"){
            steps{
                  deploy adapters: [tomcat9(credentialsId: '844041b8-98c9-44b8-9a64-a6b9ad320182', path: '', url: 'http://35.194.148.120:8080/')], contextPath: 'webapps', war: 'target/*.war'
                                       
            }
        }
    }
}
