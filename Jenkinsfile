pipeline {
    agent any 
    triggers {
        cron('H/10 * * * 1') // Triggers every 10 minutes on Mondays
    }
    stages {
        stage('Build') {
            steps {
                script {
                    // Checkout code and build with Maven
                    sh 'mvn clean package'
                }
            }
        }
        stage('Code Coverage') {
            steps {
                script {
                    // Run Jacoco to generate code coverage report
                    sh 'mvn jacoco:report'
                }
            }
        }
    }
    post {
        always {
            // Archive the coverage report
            archiveArtifacts artifacts: '**/target/site/jacoco/jacoco.xml', allowEmptyArchive: true
        }
    }
}
