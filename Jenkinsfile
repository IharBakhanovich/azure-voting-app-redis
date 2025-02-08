pipeline {
    agent any

    stages {
        
        stage('Verify branch') {
            steps {
                echo "$GIT_BRANCH"
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