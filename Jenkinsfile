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
    }
}