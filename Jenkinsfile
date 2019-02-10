/* Jenkinsfile version 2 to test Maven-Git-Tomcat build & deployment */
pipeline {
    agent any
    stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deploy to Staging'){
            steps {
                build job: 'PipelineAsCode-DeployToStaging'
            }
        }
    }
}
