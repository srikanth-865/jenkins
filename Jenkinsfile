pipeline {
    agent {
        node {
            label 'ROBOSHOP'
        }
    }


// Build section
    stages {
        stage('Build') {
            steps {
                script{
                    sh """
                       echo "Building"
                    
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
