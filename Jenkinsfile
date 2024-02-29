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
        buildDiscarder(logRotator(numToKeepStr: '3')) 
    }
    stages{


      stage('Cleaning WSpace') {
            steps {
                cleanWs() // Clean workspace before build
            }
        }

        stage('Dev Deployment'){


           steps{
            script{
                   
                sh """
                rm -rf expresso || true 
                git clone https://github.com/JQuay/expresso.git
                cd  $WORKSPACE/expresso 

        cat << EOF > expresso-shop-product/dev-values.yaml
        replicaCount: 1
        image:
          repository: hossambarakat/espresso-shop-product-catalog
          pullPolicy: IfNotPresent
          tag: ${params.webtag} 
        EOF
   """
 sh """
          cd  $WORKSPACE/expresso 
        cat << EOF > expresso-shop-reviews/dev-values.yaml
        replicaCount: 1
        image:
          repository: hossambarakat/espresso-shop-reviews
          pullPolicy: IfNotPresent
          tag: ${params.reviewstag} 
        EOF   
        """
   sh """   
        cd  $WORKSPACE/expresso 
        cat << EOF > expresso-shop-web/dev-values.yaml
        replicaCount: 1
        image:
          repository: hossambarakat/espresso-shop-web
          pullPolicy: IfNotPresent
          tag: ${params.webtag} 
        EOF
     
                   """
                   sh """
                cd $WORKSPACE/expresso

                git config --global user.name "JQuay"
                git config --global user.email "josephquayson877@gmail.com"
                
                git remote set-url origin https://JQuay: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@github.com/JQuay/https://github.com/JQuay/expresso.git

                git add -A
                git commit -m "commit from Jekins"
                git push origin main
                """
                   
            }
           }
        }

        
           
 






        stage('QA Deployment'){

            when {
                expression { params.ENVIRONMENT == 'QA' } 
            }
           steps{
            script{
                sh """
                rm -rf expresso || true 
                git clone https://github.com/JQuay/expresso.git
               

        cat <<EOF > expresso/expresso-shop-product/qa-values.yaml

                replicaCount: 1

                image:
                repository: hossambarakat/espresso-shop-product-catalog
                pullPolicy: IfNotPresent
                # Overrides the image tag whose default is the chart appVersion.
                tag: ${params.webtag} 
          EOF

        cat <<EOF > expresso/expresso-shop-reviews/qa-values.yaml

                replicaCount: 1
                image:
                repository: hossambarakat/espresso-shop-reviews
                pullPolicy: IfNotPresent
                # Overrides the image tag whose default is the chart appVersion.
                tag: ${params.reviewstag} 
          EOF
                    
        cat <<EOF > expresso/expresso-shop-web/qa-values.yaml

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
                expression { params.ENVIRONMENT == 'PreProd' } 
            }
           steps{
            script{
                sh """
                rm -rf expresso || true 
                git clone https://github.com/JQuay/expresso.git
        cat <<EOF > expresso/expresso-shop-product/preprod-values.yaml

                replicaCount: 1

                image:
                repository: hossambarakat/espresso-shop-product-catalog
                pullPolicy: IfNotPresent
                # Overrides the image tag whose default is the chart appVersion.
                tag: ${params.webtag} 
          EOF

        cat <<EOF > expresso/expresso-shop-reviews/preprod-values.yaml

                replicaCount: 1
                image:
                repository: hossambarakat/espresso-shop-reviews
                pullPolicy: IfNotPresent
                # Overrides the image tag whose default is the chart appVersion.
                tag: ${params.reviewstag} 
          EOF
                    
        cat <<EOF > expresso/expresso-shop-web/preprod-values.yaml

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
                expression { params.ENVIRONMENT == 'Prod' } 
            }
           steps{
            script{
                sh """
                rm -rf expresso || true 
                git clone https://github.com/JQuay/expresso.git
        cat <<EOF > expresso/expresso-shop-product/prod-values.yaml

                replicaCount: 1

                image:
                repository: hossambarakat/espresso-shop-product-catalog
                pullPolicy: IfNotPresent
                tag: ${params.webtag} 
        EOF

        cat <<EOF > expresso/expresso-shop-reviews/prod-values.yaml

                replicaCount: 1
                image:
                repository: hossambarakat/espresso-shop-reviews
                pullPolicy: IfNotPresent
                tag: ${params.reviewstag} 
        EOF
                    
        cat <<EOF > expresso/expresso-shop-web/prod-values.yaml

                replicaCount: 1
                image:
                repository: hossambarakat/espresso-shop-web
                pullPolicy: IfNotPresent
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