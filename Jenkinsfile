pipeline {
    agent any
   
    stages {    
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