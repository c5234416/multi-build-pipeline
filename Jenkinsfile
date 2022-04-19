pipeline {
    agent any
    tools {
        maven "localmaven"
    }
    stages {
        stage('SCM Checkout'){
            steps{
                git 'https://github.com/c5234416/mavenproject1.git'
            }
        }
        stage('MVN Build'){
            steps{
                sh "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }
        stage('MVN test'){
            steps{
                sh "mvn test"
            }
        }
        stage('test report'){
            steps{
                junit 'target/surefire-reports/*.xml'
            }
        }
        stage('archive'){
            steps{
                archiveArtifacts artifacts: 'target/*.jar'
            }
        }
    }
}
