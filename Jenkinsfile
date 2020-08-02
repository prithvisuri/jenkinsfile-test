pipeline {
    agent any
    stages {
        stage('maven-project-build') {
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo "Now Archiving the Artifacts...."
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        stage('maven-project-build'){
            steps{
                build job: 'Deploy_Application_Staging_Env'

            }
            
        }
    }
}
