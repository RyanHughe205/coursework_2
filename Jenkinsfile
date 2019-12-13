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
}
}
