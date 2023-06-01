@Library("jhc-libs") _

pipeline {
    agent any

    stages {
        stage('Git Checkout') {
            when {
                branch "develop"
            } 
            steps {
               git branch: 'main', credentialsId: 'javahometech', url: 'https://github.com/javahometech/lms'
            }
        }
        stage('Maven Build') {
            when {
                branch "develop"
            }
            steps {
               sh 'mvn clean package'
            }
        }
        
       stage('Dev deploy') {
            when {
                branch "develop"
            }
            steps {
               tomcatDeploy("ec2-user","172.31.14.235","tomcat-dev","lms")'
            } 
        }  
       stage('Stage deploy') {
            when {
                branch "stage"
            }
            steps {
               tomcatDeploy("ec2-user","172.31.14.235","tomcat-dev","lms")'
            } 
    }
    stage('Prod deploy') {
            when {
                branch "prod"
            }
            steps {
               tomcatDeploy("ec2-user","172.31.14.235","tomcat-dev","lms")'
            } 
        }
    }
 }   
    


 
