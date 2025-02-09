pipeline {
    agent any

    stages {
        
        stage('Verify branch') {
            steps {
                echo "$GIT_BRANCH"
            }
        }
      //   stage('Build Docker Image') {
      //       steps {
      //           script {
      //               // Use docker image to run the build
      //               docker.image('docker:latest').inside('--privileged') {
      //                   sh 'docker build -t my-image .'
      //               }
      //           }
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
        stage('Start test app') {
            steps {
               sh (script: """
                     # Start app line missing
                     ./scripts/test_container.psl
                  """)
            }
            post {
               success {
                  echo "App started successfully"
               }
               failure {
                  echo "App failed to start"
               }
            }
        }
        stage('Run test') {
            steps {
               sh (script: """
                     pytest ./test/test_sample.py
                  """)
            }
        }
        stage('Stop test app') {
            steps {
               sh (script: """
                     docker-compose down
                  """)
            }
        }
    }
}