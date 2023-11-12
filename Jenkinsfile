pipeline{
    agent any;
    stages{
        stage('clone my repository'){
            steps{
                git branch: 'main', url: 'https://github.com/SUJANDEMO/mavenproject.git'
            }
        }
        stage('complie code'){
            steps{
                echo "compile source code"
                sh "mvn compile" 
            }
        }
        stage('generate artifactory'){
            steps{
                echo "Generate artifactory file"
                sh "mvn package"
            }
        }
        stage ('Deployment'){
            steps{
              deploy adapters: [tomcat(credentialsId:'tomcat-credentials', path: '', url:'http://43.204.215.102:8080/')], contextPath:null, war:'**/*.war'
            }
            
        }
    }
}
