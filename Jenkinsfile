pipeline {
    agent  any;
    stages {
        stage('Preparing the environment') {
            steps {
                sh 'echo checking code quality'
            }
        }
        stage('Code Quality') {
            steps {
                sh 'echo Testing the Application'
            }
        }
        stage('Tests') {
            steps {
                sh 'python3 -m pytest'
            }
        }
   
    stage('Build') {
          agent { 
            node{
              label "DockerServer"; 
              }
          }
          steps {
              sh 'docker build https://github.com/zippeno2/chapter10.git -t chapter10:latest'
          }
      }        
      stage('Deploy') {
          agent { 
            node{
              label "DockerServer"; 
              }
          }
          steps {
              sh 'docker run -tdi -p 5000:5000 chapter10:latest'
          }
      }
    }

}

