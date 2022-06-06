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
              sh "docker build  -t marksite:v1 ."
             }
        }
        
        stage('remove last container')
        {
          steps{
              sh "docker rm -f demo"
             }
        }

        stage('start the container')
        {
            steps
            {
                sh "docker run -dit -p 80:80 --name demo  marksite:v1"
            }
        }
        
       
        stage('send mail to dev')
        {
            steps
            {
                sh "python3 sendMail.py no-error-found"
            }
        }
    }
}