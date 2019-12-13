pipeline {
         agent any
         stages {
                 stage('One') {
                 steps {
                     echo 'Hello this is Ryan'
                 }
                 }
                 stage('Two: Authentication') {
                 steps {
                    input('Continue?')
                 }
                 }                  
                  stage('Three: SonarQube') {
                   environment {
                   scannerHome = tool 'SonarQubeScanner'
                              }
                     steps {
                       withSonarQubeEnv('SonarQubeScanner') {
                             sh "${scannerHome}/bin/sonar-scanner"
                           }
                              timeout(time: 10, unit: 'MINUTES') 
                              {
                              waitForQualityGate abortPipeline: true
                                                                     }
                            }
                       }    
                  
                         stage('Four: Build image') {
 
        app = docker.build("https://github.com/RyanHughe205/coursework_2")                      
                  }    


    stage('Five: Push image') {
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
}
}
