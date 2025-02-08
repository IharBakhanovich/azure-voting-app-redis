pipeline {
    agent any

    stages {
        
        stage('Verify branch') {
            steps {
                echo "$GIT_BRANCH"
            }
        }
        stage('Build Docker Image') {
            agent {
                docker {
                    image 'docker:latest'
                    args '--privileged'  // This is required for Docker-in-Docker
                }
            }
            steps {
                sh 'docker build -t my-image .'
            }
        }
      //   stage('Build Docker Image') {
      //       steps {
      //           sh 'docker build -t my-image .'
      //       }
      //   }
        stage('Check Docker') {
            steps {
                sh 'which docker || echo "Docker not found!"'
                sh 'docker --version || echo "Docker not installed!"'
            }
        }
        stage("Docker Build"){
         steps{
            sh(script: 'docker images -a')
            sh(script: """
                cd azure-vote/
                docker images -a
                docker build -t jenkins-pipeline .
                docker images -a
                cd ..
            """)
         }

        }
    
      //   stage('Goodbye') {
      //       steps {
      //           echo 'Bye bye'
      //       }
      //   }
      //   stage('Powershell') {
      //       steps {
      //           echo "Hello from Terminal!"
      //       }
      //   }
    }
}