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
        timeout(time: 15, unit: 'MINUTES')
    }

    parameters {                             // inputs asked at build time
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: '...')
        booleanParam(name: 'DEPLOY', defaultValue: true, description: '...')
        choice(name: 'CHOICE', choices: ['One','Two','Three'], description: '...')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: '...')
    }

// Build section
    stages {
        stage('Build') {
            steps {
                script{
                    sh """
                       echo "Building"
                       echo "Course is ${COURSE}"
                       echo "${params.PERSON}"
                        echo "${params.DEPLOY}"
                         echo "${params.CHOICE}"
                          echo "${params.PASSWORD}"
                    
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
             input {
                message "Do you want to proceed to deployment?"
                ok "Approve Deployment"
                submitter "admin,release-team" // Optional: Restrict who can approve
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'WHo should i say hello')
                }
             }
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