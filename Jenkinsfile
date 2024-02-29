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
            defaultValue: 'latest',
            description: 'Enter the review image tag.'
        )
        string(
            name: 'prodtag',
            defaultValue: 'latest',
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

        cat <<EOF > $WORKSPACE/expresso-shop-product/dev-values.yaml

                replicaCount: 1

                image:
                repository: hossambarakat/espresso-shop-product-catalog
                pullPolicy: IfNotPresent
                # Overrides the image tag whose default is the chart appVersion.
                tag: ${params.webtag} 
          EOF

        cat <<EOF > $WORKSPACE/expresso-shop-reviews/dev-values.yaml

                replicaCount: 1
                image:
                repository: hossambarakat/espresso-shop-reviews
                pullPolicy: IfNotPresent
                # Overrides the image tag whose default is the chart appVersion.
                tag: ${params.reviewstag} 
          EOF
                    
        cat <<EOF > $WORKSPACE/expresso-shop-web/dev-values.yaml

                replicaCount: 1
                image:
                repository: hossambarakat/espresso-shop-web
                pullPolicy: IfNotPresent
                # Overrides the image tag whose default is the chart appVersion.
                tag: ${params.webtag} 
          EOF
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
        cat <<EOF > $WORKSPACE/expresso-shop-product/dev-values.yaml

                replicaCount: 1

                image:
                repository: hossambarakat/espresso-shop-product-catalog
                pullPolicy: IfNotPresent
                # Overrides the image tag whose default is the chart appVersion.
                tag: ${params.webtag} 
          EOF

        cat <<EOF > $WORKSPACE/expresso-shop-reviews/dev-values.yaml

                replicaCount: 1
                image:
                repository: hossambarakat/espresso-shop-reviews
                pullPolicy: IfNotPresent
                # Overrides the image tag whose default is the chart appVersion.
                tag: ${params.reviewstag} 
          EOF
                    
        cat <<EOF > $WORKSPACE/expresso-shop-web/dev-values.yaml

                replicaCount: 1
                image:
                repository: hossambarakat/espresso-shop-web
                pullPolicy: IfNotPresent
                # Overrides the image tag whose default is the chart appVersion.
                tag: ${params.webtag} 
          EOF
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
        cat <<EOF > $WORKSPACE/expresso-shop-product/dev-values.yaml

                replicaCount: 1

                image:
                repository: hossambarakat/espresso-shop-product-catalog
                pullPolicy: IfNotPresent
                # Overrides the image tag whose default is the chart appVersion.
                tag: ${params.webtag} 
          EOF

        cat <<EOF > $WORKSPACE/expresso-shop-reviews/dev-values.yaml

                replicaCount: 1
                image:
                repository: hossambarakat/espresso-shop-reviews
                pullPolicy: IfNotPresent
                # Overrides the image tag whose default is the chart appVersion.
                tag: ${params.reviewstag} 
          EOF
                    
        cat <<EOF > $WORKSPACE/expresso-shop-web/dev-values.yaml

                replicaCount: 1
                image:
                repository: hossambarakat/espresso-shop-web
                pullPolicy: IfNotPresent
                # Overrides the image tag whose default is the chart appVersion.
                tag: ${params.webtag} 
          EOF
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
        cat <<EOF > $WORKSPACE/expresso-shop-product/dev-values.yaml

                replicaCount: 1

                image:
                repository: hossambarakat/espresso-shop-product-catalog
                pullPolicy: IfNotPresent
                # Overrides the image tag whose default is the chart appVersion.
                tag: ${params.webtag} 
          EOF

        cat <<EOF > $WORKSPACE/expresso-shop-reviews/dev-values.yaml

                replicaCount: 1
                image:
                repository: hossambarakat/espresso-shop-reviews
                pullPolicy: IfNotPresent
                # Overrides the image tag whose default is the chart appVersion.
                tag: ${params.reviewstag} 
          EOF
                    
        cat <<EOF > $WORKSPACE/expresso-shop-web/dev-values.yaml

                replicaCount: 1
                image:
                repository: hossambarakat/espresso-shop-web
                pullPolicy: IfNotPresent
                # Overrides the image tag whose default is the chart appVersion.
                tag: ${params.webtag} 
          EOF
                   """
            }
           }
        }





        //  stage('Cleaning WSpace') {
        //     steps {
        //         cleanWs() // Clean workspace before build
        //     }
        // }
    }
}