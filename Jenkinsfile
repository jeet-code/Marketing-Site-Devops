IS_ERROR=0

pipeline {
    agent any

    stages {
        stage('cloning the repo') {
            steps {
                shell("git clone https://github.com/jeet-code/Marketing-Site-Devops")
            }
        }
        
        stage('build image')
        {
          steps{
              sh ""
             }
        }
        
        stage('send error mail')
        {
            when {
             expression { IS_ERROR == 0}
            }
            steps
            {
                sh "python3 cf-test/sendMail.py error-found"
            }
        }
        
        stage('send test pass mail')
        {
            when {
             expression { IS_ERROR != 0 }
            }
            steps
            {
                sh "bash /var/lib/jenkins/workspace/cf-check-teat/cf-test-1/getDet.sh"
                sh "python3 cf-test/sendMail.py no-error-found"
            }
        }
        
        stage('push to master')
        {
            when {
             expression { IS_ERROR != 0 }
            }
            steps
            {
                sh "bash /var/lib/jenkins/workspace/cf-check-teat/cf-test-1/getAllStacks.sh"
                echo "push to master"
            }
        }
    }
}