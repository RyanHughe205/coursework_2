pipeline {
         agent any
         stages {
                 stage('One') {
                 steps {
                     echo 'Hello this is Ryan'
                 }
                 }
                 stage('Two') {
                 steps {
                    input('Continue?')
                 }
                 }
                 stage('Three') {
                 when {
                       not {
                            branch "master"
                       }
                 }
                 steps {
                       echo "Hello world"
                 }
                 }
                 
         }     
}
