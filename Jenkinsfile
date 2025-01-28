pipeline {
    agent any
   
    stages {
        stage("checkout") {
            steps {
                bat 'dir'
                git branch:'main', url: 'https://github.com/Sh37ma/course3-jenkins-gs-spring-petclinic'
                bat 'dir'
            }
            
        }
    
        stage("build") {
            steps {
                bat "mvn package"
            }
        }
        
        stage("capture") {
            steps {
                archiveArtifacts '**\\target\\*.jar'
                junit stdioRetention: '', testResults: '**\\target\\surefire-reports\\TEST*.xml'
                jacoco()
            }
        }
    }
    
    post {
        always {
            emailext body: '', recipientProviders: [developers()], subject: '', to: 'osk@hehe.com'
        }
    }
        
}