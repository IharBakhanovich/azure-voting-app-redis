pipeline {
    agent any

    stages {
        
        stage('Get Branch Name') {
            steps {
                script {
                    def branch = sh(script: 'git rev-parse --abbrev-ref HEAD', returnStdout: true).trim()
                    echo "Branch Name: ${branch}"
                }
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