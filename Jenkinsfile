pipeline{

    agent any 
    parameters {
        choice(
            name: 'ENVIRONMENT',
            choices: ['Dev', 'QA', 'PreProd', 'Prod'],
            description: 'Select the environment to deploy to.'
        )
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

         stage('Preparation') {
            steps {
                cleanWs() // Clean workspace before build
            }
        }
    }
}