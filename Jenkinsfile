pipeline{

    agent any 
    parameters {
        choice(
            name: 'ENVIRONMENT',
            choices: ['Dev', 'QA', 'PreProd', 'Prod'],
            description: 'Select the environment to deploy to.'
        )
    }

      options {
        buildDiscarder(logRotator(numToKeepStr: '3')) // Keeps the last 10 builds
    }
    stages{
        stage('first'){

            when {
                expression { params.ENVIRONMENT == 'Dev' } // Only deploy if environment is not Dev
            }
           steps{
            script{
                sh """
                    echo "Deploying to ${params.ENVIRONMENT} environment..."
                   """
            }
           }
        }


        stage('second'){

            when {
                expression { params.ENVIRONMENT == 'QA' } // Only deploy if environment is not Dev
            }
           steps{
            script{
                sh """
                    echo "Deploying to ${params.ENVIRONMENT} environment..."
                   """
            }
           }
        }


        stage('third'){

            when {
                expression { params.ENVIRONMENT == 'PreProd' } // Only deploy if environment is not Dev
            }
           steps{
            script{
                sh """
                    echo "Deploying to ${params.ENVIRONMENT} environment..."
                   """
            }
           }
        }
 stage('fourth'){

            when {
                expression { params.ENVIRONMENT == 'Prod' } // Only deploy if environment is not Dev
            }
           steps{
            script{
                sh """
                    echo "Deploying to ${params.ENVIRONMENT} environment..."
                   """
            }
           }
        }





         stage('Cleaning WSpace') {
            steps {
                cleanWs() // Clean workspace before build
            }
        }
    }
}