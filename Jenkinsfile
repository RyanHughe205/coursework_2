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
                  stage('Three: Sonarqube') {
                   environment {
                   scannerHome = tool 'SonarQube'
                              }
                     steps {
                       withSonarQubeEnv('sonarqube') {
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
