pipeline {
    agent any
    stages {
      stage("Build"){
        steps {
          sh 'npm install'
        }
      }
      stage("Test"){
         steps {
           echo 'Tests pas encore prets'
        }
      }
      /*stage("Push"){
         steps{
           script{
             docker.withRegistry('https://registry.hub.docker.com','DockerHub'){
               def customImage = docker.build(" remaoun/lamine-chakibProject")
               customImage.push()
             }*/
           }
        }
      }
    }
}
