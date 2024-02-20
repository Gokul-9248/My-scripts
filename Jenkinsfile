pipeline{
    agent any
    stages{
        stage('checkout the code from github'){
            steps{
                 git url: 'https://github.com/Gokul-9248/star-agile-health-care.git'
                 echo 'github url checkout'
            }
        }
        stage('codecompile'){
            steps{
                echo 'starting compiling'
                sh 'mvn compile'
            }
        }
        stage('codetesting'){
            steps{
                sh 'mvn test'
            }
        }
        stage('qa'){
            steps{
                sh 'mvn checkstyle:checkstyle'
            }
        }
        stage('package'){
            steps{
                sh 'mvn package'
            }
        }
         
         
         stage('run dockerfile'){
          steps{
               sh 'docker build -t myimg .'
           }
         }
         
         stage('port expose and container creation'){
          steps{
               sh 'docker run -itd -p 8091:8082 --name My-container myimg'
           }
         }
         
    }
}
