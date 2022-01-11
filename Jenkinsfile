pipeline {
    agent any
    triggers{ cron('H/1 * * * *') }
    stages {
        stage('build') {
            steps {
                build 'job1'
            }
        }
        stage('Deploy') {
            steps {
                build 'job3'
            }
        }
        stage('Test') {
            steps {
                build 'job1'
            }
        }
        stage('Release') {
            steps {
                build 'job2'
            }
        }
        
    }
    post{
        failure{
           build 'job2'
        }
        success{
            build 'job3'
        }
    }
    
}
