pipeline {
    agent any
    stages {
        stage('maven-project-build') {
            steps {
                sh 'mvn -f pon.xml clean package'
            }
            post {
                success {
                    echo "Now Archiving the Artifacts...."
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        stage('maven-porject-deploy'){
            steps{
                build job: 'maven-porject-deploy'

            }
            
        }
        stage('maven-project-prod'){
            steps{
                timeout(time:5, unit:'DAYS'){
                    input message:'Approve PRODUCTION Deployment?'
                }
                build job: 'maven-project-prod'
            }
        }
    }
}
