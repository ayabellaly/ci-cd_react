pipeline {
  agent any
   stages {
        stage('Build') {
          steps {
           bat 'docker build -t aya20/my-nodejs-app:latest ./client'
           bat 'docker build -t aya20/rjs-app:latest ./server'
            }
         }

     stage('Test') {
            steps {
                script {
                    // Run tests for the server
                    bat 'docker run --rm aya20/my-nodejs-app:latest npm test'

                    // Run tests for the client
                    bat 'docker run --rm aya20/rjs-app:latest npm test'
                }
            }
        }
        stage('Push') {
         steps{
               withDockerRegistry([credentialsId: "aya-dockerhub", url: ""])
               {
                  bat 'docker push aya20/rjs-app:latest'
                  bat 'docker push aya20/my-nodejs-app:latest'
               }
         } 
      }
    }
   }