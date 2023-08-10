pipeline {
    agent{
        lable 'jdk-17'
    }
    options {
        timeout( time: 30, unit: 'MINUTES')
    }
    triggers{
        pollSCM('* * * * *')
    }
    tools {
        jdk 'java-17'
    } 
    stages {
        stage('git') {
            steps {
            git branch: 'develop', url: 'https://github.com/manikantaQTDEVOPS/spring-petclinic_july.git'
            }
              
        }
        stage('build and package') {
            steps {
                sh script: 'mvn package'
            }
        }
        stage('reporting') {
            steps {
                  archiveArtifacts artifacts: '**/target/spring-petclinic-*.jar'
                  junit testResults: '**/target/surefire-reports/TEST-*.xml'  
            }
        }
    }   

    }
