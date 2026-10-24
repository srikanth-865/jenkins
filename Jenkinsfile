pipeline {
    agent {
        node {
            label 'ROBOSHOP' //we gave in jenkins UI for to match label for this name to run this pipeline
        }
    }

     environment {                       // variables for every stage,its a global variable
        COURSE = "Jenkins"
    }

    options {                                // pipeline-wide behaviour
        disableConcurrentBuilds()   //only onebuild runs at a time
        timeout(time: 15, unit: 'MINUTES') // build complete atleas 15min
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
            // second time applied
                when {
                // Evaluates the boolean parameter directly
                expression { "${params.DEPLOY}" == "true" }
            }
// first time applied
             /* input {  // for approve any person we use input they approve in console true then deployment started
                message "Do you want to proceed to deployment?"
                ok "Approve Deployment"
                submitter "admin,release-team" // Optional: Restrict who can approve
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'WHo should i say hello')
                }
             } */

            steps {
                script{
                    sh """
                       echo "Deploying"
                    
                    """
                       }
            }
        }
    }
    // it always execute this post build even pipeline fails also
 post{
    always{
        echo 'i  always say hello again'
    }
    success {
            echo 'Build is succeeded!'
        }
        failure {
            echo 'Build is  failed!'
            
        }
     }
}