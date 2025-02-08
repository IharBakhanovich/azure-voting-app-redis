pipeline {
    agent any

    stages {
        stages {
        stage('Checkout') {
            steps {
                checkout scm
                echo "Branch Name: ${env.BRANCH_NAME}"
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