pipeline {
    agent {
        node {
            label 'ROBOSHOP'
        }
    }

     environment {                       // variables for every stage,its a global variable
        COURSE = "Jenkins"
    }

    options {                                // pipeline-wide behaviour
        disableConcurrentBuilds()  
        timeout(time: 1, unit: 'SECONDS')
    }


// Build section
    stages {
        stage('Build') {
            steps {
                script{
                    sh """
                       echo "Building"
                       echo "Course is ${COURSE}"
                       sleep 5
                    
                    """
                       }
                }
                 
            }
        stage('Test') {
            steps {
                script{
                    sh """
                       echo "Testing"
                    
                    """
                       }
            }
        }
        stage('Deploy') {
            steps {
                script{
                    sh """
                       echo "Deploying"
                    
                    """
                       }
            }
        }
    }
 post{
    always{
        echo'i  always say hello agaain'
    }
    success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed!'
            
        }
     }
    }
