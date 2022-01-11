pipeline {
    agent any
    triggers{ cron('H/1 * * * *') }
    stages {
        stage('build') {
            steps {
                when {
                    beforeAgent true
                    branch 'master'
                }
                build 'job1'
            }
        }
        stage('Deploy') {
            steps {
                build 'job2'
            }
        }
        stage('Test') {
            steps {
                build 'job2'
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
