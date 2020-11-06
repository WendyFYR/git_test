pipeline {
    agent any
    environment{
     SONAR_HOME = "${tool 'SonarScanner 4.0'}"
     PATH="${env.SONAR_HOME}/bin:${env.PATH}"
    }
     
    
  	stage("build & SonarQube analysis") { 
             steps { 
                  withSonarQubeEnv('sonarserver') {
                  sh "sonar-scanner"
                 }
   			 }
    }
    
      stage("Quality Gate") {
            steps {
              timeout(time: 1, unit: 'HOURS') {
                waitForQualityGate abortPipeline: true
              }
            }
          }
           
}
