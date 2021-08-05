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
          sh '/usr/bin/jmeter/apache-jmeter-5.1.1/bin/jmeter -n -t apptest.jmx -l results.jtl'
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
