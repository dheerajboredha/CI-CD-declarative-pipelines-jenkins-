pipeline {
    agent {
        label 'Java'
    }

    triggers {
        pollSCM('* * * * *')
    }

    stages {
        stage('git repo') {
            steps {
                git url: 'https://github.com/spring-projects/spring-petclinic.git', branch: 'main'
                    
            }
        }

        stage('build') {
            steps{
                sh 'mvn package'
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: '**/target/*.jar'
            junit '**/target/surefire-reports/*.xml'
        }
        success {
            echo 'this pipeline good'
        }
        failure {
            echo 'this is waste pipeline'
        }
    }
}