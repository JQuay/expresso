pipeline{

    agent any 
    parameters {
        choice(
            name: 'ENVIRONMENT',
            choices: ['Dev', 'QA', 'PreProd', 'Prod'],
            description: 'Select the environment to deploy to.'
        )

        string(
            name: 'webtag',
            defaultValue: 'latest',
            description: 'Enter the web image tag .'
        )
        string(
            name: 'reviewstag',
            defaultValue: '',
            description: 'Enter the review image tag.'
        )
        string(
            name: 'prodtag',
            defaultValue: '',
            description: 'Enter the product image tag.'
        )
    }

      options {
        buildDiscarder(logRotator(numToKeepStr: '3')) // Keeps the last 10 builds
    }
    stages{
        stage('Dev Deployment'){

            when {
                expression { params.ENVIRONMENT == 'Dev' } // Only deploy if environment is not Dev
            }
           steps{
            script{
                   
                sh """
                cd   $WORKSPACE/expresso/expresso-shop-product

                ls -l
                   
                   """
                   
            }
           }
        }


        stage('QA Deployment'){

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


        stage('Preprod Deployment'){

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
 stage('Production Deployment'){

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