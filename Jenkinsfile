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
          cd '/home/lamine/jmeter'
          sh '/home/lamine/jmeter -n -t plan-appTest.jmx -l results.jtl'
          sh 'cat results.jtl'
          perfReport 'results.jtl'
        }
      }
      stage("Push"){
         steps{
           script{
             docker.withRegistry('https://registry.hub.docker.com','DockerHub'){
               def customImage = docker.build(" remaoun/lamine-chakibProject")
               customImage.push()
             }
           }
        }
      }
    }
}
